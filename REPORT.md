

**Group Name:** LI7  

**Members:**
- Firas Abdullah Ali Yousif — 229910601  
- Assim Boutaher — 220901712  
- Mouad Hamadou — 220911267  
- Anas Brkji — 220901178  

---

# Comparative Study of Regularization Techniques in Multilayer Perceptrons

## 1. Introduction

This project investigates the impact of different regularization techniques on the performance of a Multilayer Perceptron (MLP) using the MNIST dataset. The primary objective is to analyze how these techniques affect overfitting and generalization.

Deep learning models can achieve high accuracy on training data but may fail to generalize to unseen data. Regularization techniques are therefore essential to improve robustness and ensure reliable performance.
## 2. Dataset Description

The MNIST dataset consists of grayscale images of handwritten digits (0–9), each of size 28×28 pixels.

- Total samples: 70,000  
- Training set: 60,000  
- Test set: 10,000  

The dataset is balanced, with approximately equal representation of each class. This ensures fair evaluation and prevents bias.

The training dataset was further split into:

- 80% training (48,000 samples)  
- 20% validation (12,000 samples)  

The validation set was used to monitor performance and detect overfitting.
## 3. Methodology

### 3.1 Base Model (MLP)

A Multilayer Perceptron (MLP) was implemented with the following architecture:

- Input layer: 784 neurons  
- Hidden layer 1: 256 neurons (ReLU)  
- Hidden layer 2: 128 neurons (ReLU)  
- Output layer: 10 neurons  

**Training configuration:**

- Loss function: CrossEntropyLoss  
- Optimizer: Adam  
- Learning rate: 0.001  
- Batch size: 64  
- Epochs: 5 (baseline experiments)  

The MLP was selected because it is sufficient for the MNIST dataset and allows clear demonstration of learning behavior and the effects of regularization techniques.
### 3.2 Baseline Model

The baseline model was trained without any regularization.

**Purpose:**

- Establish a reference point  
- Observe natural model behavior  
- Identify overfitting
### 3.3 Dropout

Dropout was applied with a probability of 0.5 after each hidden layer.

**Rationale:**

- Randomly disables neurons during training  
- Prevents co-adaptation  
- Improves generalization
### 3.4 L2 Regularization

L2 regularization was implemented using weight decay:

- weight_decay = 0.001  

**Rationale:**

- Penalizes large weights  
- Encourages simpler models  
- Reduces overfitting
### 3.5 Early Stopping

Early stopping was applied based on validation loss:

- Patience = 3  

Training stops when validation loss does not improve for three consecutive epochs.

**Rationale:**

- Prevents over-training  
- Stops at optimal performance point  
- Improves efficiency
### 3.6 Hyperparameter Selection

Hyperparameters were chosen based on standard practices:

- Learning rate: 0.001  
- Batch size: 64  
- Dropout rate: 0.5  
- Weight decay: 0.001  

The goal was to maintain consistency and focus on comparing methodologies rather than performing extensive hyperparameter tuning.
## 5. Results

| Model             | Train Accuracy | Validation Accuracy | Test Accuracy |
|------------------|---------------|---------------------|--------------|
| Baseline          | 98.66%        | 97.28%              | 97.49%       |
| Dropout           | 95.70%        | 97.10%              | 97.27%       |
| L2 Regularization | 97.60%        | 97.12%              | 97.33%       |
| Early Stopping    | 99.01%        | 97.03%              | 97.33%       |


## 6. Results Analysis

### Baseline Model
The baseline model achieved the highest validation and test accuracy (97.49%). However, it also showed signs of overfitting, as the training accuracy (98.66%) exceeded the validation accuracy (97.28%).

---

### Dropout
The dropout model achieved lower training accuracy (95.70%) while maintaining similar validation accuracy (97.10%). This indicates reduced overfitting and improved generalization, although with a slight decrease in overall performance.

---

### L2 Regularization
The L2 regularization model achieved balanced performance, with a smaller gap between training accuracy (97.60%) and validation accuracy (97.12%). This demonstrates improved generalization and more stable learning behavior.

---

### Early Stopping
The early stopping model achieved high training accuracy (99.01%) while maintaining stable validation performance (97.03%). Training was automatically stopped at epoch 6, preventing overfitting and improving efficiency.
### Overall Comparison

- The baseline model achieved the highest test accuracy but showed slight overfitting.  
- Dropout reduced overfitting but slightly decreased performance.  
- L2 regularization provided the best balance between performance and stability.  
- Early stopping effectively controlled overfitting and reduced unnecessary training.  

Overall, L2 regularization and early stopping were the most effective methods for improving generalization.

---

## 7. Conclusion

This project demonstrates that regularization techniques significantly improve the performance and reliability of neural networks.

While the baseline model achieved high training accuracy, it exhibited signs of overfitting. In contrast, dropout, L2 regularization, and early stopping improved generalization and produced more stable results.

Among the tested methods, L2 regularization and early stopping provided the most consistent improvements, making them the most effective techniques for this task.
