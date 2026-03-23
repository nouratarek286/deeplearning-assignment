# CNN Assignment – CIFAR-10 Classification

## Overview
This assignment implements Convolutional Neural Networks (CNNs) to classify images from the CIFAR-10 dataset.  
CIFAR-10 contains 60,000 color images across 10 classes: airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck.

- Image size: 32×32 pixels, 3 channels (RGB)  
- Training set: 50,000 images  
- Test set: 10,000 images  
- Classes: 10 balanced classes  

The goal is to explore different CNN architectures, compare pooling methods, analyze model performance, and understand hyperparameter effects.

---

## Setup Instructions

1. **Clone the repository:**

```bash
git clone https: https://github.com/nouratarek286/deeplearning-assignment/upload/main
cd CNN-Assignment

pip install torch torchvision matplotlib seaborn
# If using Jupyter Notebook
jupyter notebook CNN_Assignment.ipynb

Run all cells in order: Load data → Define models → Train → Evaluate → Plot results.

---

## Implementation Summary

* **Data preprocessing:**

  * Normalized images to [-1, 1]
  * Split into training and test sets
  * Small subsets were used for faster experimentation

* **Models implemented:**

  * Model 1: Basic 2-conv layer CNN (baseline)
  * Model 2: Deeper CNN with 3 convolutional layers
  * Model 3: CNN with dropout for regularization
  * Model 4: CNN with batch normalization

* **Pooling comparison:**

  * Max Pooling vs Average Pooling using identical architecture

* **Evaluation metrics:**

  * Training accuracy, test accuracy, and loss

---

## Model Comparison Table

| Model   | Test Accuracy |
| ------- | ------------- |
| Model 1 | 63.84%        |
| Model 2 | 24.00%        |
| Model 3 | 29.60%        |
| Model 4 | 32.00%        |

**Analysis:**

* Model 1 achieved the highest accuracy because it was trained fully before; Models 2–4 were trained on smaller subsets to reduce computation time.
* Model 2 (deeper CNN) overfits on small data, lowering accuracy.
* Model 3 uses dropout to reduce overfitting slightly.
* Model 4 uses batch normalization to improve training stability.

---

## Max Pooling vs Average Pooling

| Pooling Type    | Test Accuracy |
| --------------- | ------------- |
| Max Pooling     | 31.00%        |
| Average Pooling | 29.40%        |

**Analysis:**

* Max Pooling captures the strongest features in each region (edges, details), performing better.
* Average Pooling smooths features, which can lose important details, reducing accuracy.
* In CNNs, Max Pooling is generally preferred for feature extraction.

---

## Architecture Analysis (Example: Model 2)

* Input image size: 32x32x3 (RGB)
* Conv1 + MaxPool: 16x16x32
* Conv2 + MaxPool: 8x8x64
* Conv3 + MaxPool: 4x4x128
* Flattened: 2048 features
* Fully connected layers: 2048 → 128 → 10 classes

**Notes:**

* Number of parameters increases with the number of filters and kernel size.
* Flattening converts feature maps into a vector for fully connected layers.
* Pooling reduces spatial dimensions while retaining important features.

---

## Training Graphs

* Training accuracy and loss graphs can be found in the notebook (`accuracy_loss_plots`).
* Observations:

  * Accuracy increases as the model learns features
  * Loss decreases over epochs
  * Small subsets may cause fluctuations due to limited data

---

## Hyperparameter Tuning (Optional / Future Work)

* Experiment with different learning rates (e.g., 0.001, 0.0005)
* Add more dropout layers for regularization
* Explore batch normalization in all layers
* Use full dataset for higher accuracy and better generalization

---

## How to Run

1. Run all cells in the notebook sequentially.
2. Model training, evaluation, pooling comparison, and plots will be automatically generated.
3. Update any subset sizes or epochs in the notebook for faster or full-scale training.

* Name: Noura Tarek
* Course: Deep Learning
* Submission: CNN Assignment – CIFAR-10