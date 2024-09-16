# Melanoma Skin Detection Assignment using CNN by Vimala Subramanian
>Problem statement: To build a CNN based model which can accurately detect melanoma. Melanoma is a type of cancer that can be deadly if not detected early. It accounts for 75% of skin cancer deaths. A solution which can evaluate images and alert the dermatologists about the presence of melanoma has the potential to reduce a lot of manual effort needed in diagnosis.


## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Conclusions](#conclusions)
* [Acknowledgements](#acknowledgements)

<!-- You can include any other section that is pertinent to your problem -->

## General Information

The CNN model is built using a dataset which consists of 2357 images of malignant and benign oncological diseases, which were formed from the International Skin Imaging Collaboration (ISIC). All images were sorted according to the classification taken with ISIC, and all subsets were divided into the same number of images, with the exception of melanomas and moles, whose images are slightly dominant.
The data set contains the following diseases:
Actinic keratosis
Basal cell carcinoma
Dermatofibroma
Melanoma
Nevus
Pigmented benign keratosis
Seborrheic keratosis
Squamous cell carcinoma
Vascular lesion
However the class data was imbalanced. Augmentor was used to generate 500 images of each class so that some balance is achieved.

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->

## Conclusions


- **Conclusion 1 from the initial Model**
accuracy: 0.8700 - loss: 0.3415 - val_accuracy: 0.4877 - val_loss: 2.3936
1. The **training accuracy is 87%** and **Validation accuracy is 48.77%**.
2. The training and Validation Loss are  .3415 and 2.3936 which is a huge gap.
3. The training loss is decreasing while the validation_loss is increasing
4. Overfitting: There is huge difference and clearly calls out on overfitting. The model has memorized the training data rather than generalizing well.

- **Conclusion 2 from the model after data augmentation and handling data imbalance**

Train Data Analysis
accuracy: 0.9413 - loss: 0.1651 - val_accuracy: 0.6941 - val_loss: 1.9756 Inference The training accuracy is high (94.13%), but the validation accuracy is significantly lower (69.41%), and the validation loss is quite high (1.9756). This indicates overfitting, where the model performs well on the training data but poorly on unseen validation data.

Reasons for overfitting
1. Too Complex Model: The model may have too many layers or filters, giving it excessive capacity to memorize the training data but not generalize to new data.
2. Insufficient Regularization: Dropout, weight regularization (L2), or data augmentation might not be enough or could be missing, allowing the model to overfit. Though we have handled data imbalance still the model overfits.
3. Small Training Data: If your training dataset is small, the model can easily overfit by memorizing the small dataset rather than learning general patterns.

Steps to address overfitting
1. Increase Data Augmentation: Add more variations to the input data to help the model generalize better.
2. Reduce Model Complexity: Simplify the model by reducing the number of filters or layers.
3. Increase Dropout: Increase the dropout rate in fully connected layers to regularize the model and prevent overfitting:
4. L2 Regularization: Add L2 regularization to penalize large weights and encourage the model to find simpler solutions:
5. Early Stopping: Use early stopping to avoid overtraining. It can help you stop training when the validation loss starts increasing: ex: early_stopping = tf.keras.callbacks.EarlyStopping(monitor='val_loss', patience=3, restore_best_weights=True)
6. Reduce Learning Rate: A high learning rate might cause the model to "overfit" the data too quickly. Try reducing the learning rate:

- **Conclusion 3 from the test data**
Inference from test data
The model's accuracy on the test set is quite low (36.44%), and the loss is very high (8.4024), suggesting that the model is struggling to generalize to unseen data. Let's analyze this and consider some strategies to improve the performance.

Key Observations:

1. Overfitting: The validation accuracy is significantly lower than the training accuracy, indicating that the model is overfitting to the training data.
2. Class Imbalance: It’s possible that some classes in your dataset might have fewer examples than others, which can cause the model to be biased towards the majority classes.
3. High Loss & Poor Predictions: The model seems uncertain in its predictions, leading to a high loss despite reasonable accuracy on a small part of the data.

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->


## Technologies Used
- Python
- Tensforflow
- Augmentor

<!-- As the libraries versions keep on changing, it is recommended to mention the version of library used in this project -->


## Contact
Created by [@vimalasuchi] - feel free to contact me!


<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->
