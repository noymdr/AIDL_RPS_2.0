# Rock-Paper-Scissors Image Classification

## 🚀 Project Summary

This project develops an image classification model for Rock-Paper-Scissors using deep learning and transfer learning. It aims to accurately classify hand gestures into 'rock', 'paper', or 'scissors', demonstrating the power of fine-tuned pre-trained networks for image recognition tasks. This serves as a practical example for human-computer interaction and basic gesture recognition systems.

## 📊 Dataset Description

The dataset is sourced from Kaggle's Rock-Paper-Scissors collection. It underwent a two-stage splitting process: initially into training and validation sets, then the training set was further divided to carve out a dedicated test set. All splits maintained class stratification and were organized into `final_train`, `validation`, and `test` directories. Preprocessing involved resizing images to 224x224 pixels and normalizing pixel values. Extensive data augmentation (rotation, shifting, zooming, flipping, brightness) was applied to the training set, while validation and test sets only received normalization.

## 🧠 Model and Methods

The model employs transfer learning using a pre-trained VGG16 network (ImageNet weights) as a frozen feature extractor. A custom classification head, consisting of Global Average Pooling and two Dense layers (512 units with ReLU, and 3 units with Softmax), was appended. The model was compiled with the AdamW optimizer, categorical cross-entropy loss, and accuracy as the primary metric. Training utilized early stopping based on validation loss and model checkpointing to save the best-performing iteration.

## 📈 Results and Analysis

### Model Performance

The model achieved an exceptional test accuracy of 99.75% and a perfect validation accuracy of 100%. These high percentages indicate that the model generalized extremely well to unseen data, successfully classifying almost all rock-paper-scissors gestures. The confusion matrices for both sets confirm this outstanding performance, showing very high numbers along the main diagonal and minimal off-diagonal elements, suggesting virtually no misclassifications between the classes. This robust performance indicates the VGG16-based model is highly reliable for this specific image classification task.

**Confusion Matrix (Test Set):**

<p align="center">
  <img width="488" height="400" alt="image" src="https://github.com/user-attachments/assets/032414b7-9511-4f06-a50e-faf01788af1f" />
</p>

**Confusion Matrix (Validation Set):**

<p align="center">
  <img width="479" height="401" alt="image" src="https://github.com/user-attachments/assets/b01753f3-c060-4843-9d29-50116842f492" />
</p>

### Why the High Accuracy?

This high accuracy can be attributed to several factors: the task's simplicity with distinct hand gestures, effective transfer learning from VGG16's pre-trained weights, high data quality and consistency, and robust generalization due to data augmentation.

### Overfitting/Underfitting

Given the high accuracy on both training (implied) and validation/test sets, there are no clear signs of underfitting. While metrics are almost perfect, extensive data augmentation and `EarlyStopping` with `restore_best_weights` during training were specifically designed to combat overfitting. The slight increase in validation loss in the final epochs after its minimum suggests `EarlyStopping` prevented significant overfitting, indicating the model is well-generalized.

### Suggestions for Future Improvements

1.  **Test with More Diverse Real-World Data:** Future work should involve testing the model on more varied live camera feeds or datasets, including different lighting, backgrounds, hand sizes, and angles, to truly assess robustness and generalization in practical scenarios.
2.  **Explore Other Pre-trained Architectures:** While VGG16 performed admirably, investigating other modern architectures, like ResNet, could offer better trade-offs in terms of performance and computational efficiency, especially for potential deployment.
3.  **Refine Data Augmentation:** Experimenting with different data augmentation strategies or parameters could lead to slight improvements or increased robustness against specific types of noise.
