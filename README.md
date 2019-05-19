# Dog Breed Identification

This project tries to identify the breed of dog using convolutional neural networks and a pre-trained Resnet50 neural network.

### Prerequisits:

please refere to the <a href='requirements'>requirements</a> folder and choose the appropriate file depend on operating system and whether you use a gpu or not.

### Description:

Here, I am trying to identify the dog breed from dog images and if is a human image it will provide an estimate of the dog breed that is most resembling using a neural network built with Keras from a scratch and compare the accuracy with another one built upon <a target='_blank' href='https://arxiv.org/pdf/1512.03385.pdf'>Resnet50</a>.
The pre-trained gives a much better accuracy and result

### Model Architecture:

There were two models, the first one is built from scratch using Keras as following:
1. 3 convolutional layers with filters(16, 32, 64) respectively, each filter is 2x2 and padding is 'same' so not lose any features in the picture and the first layer of them is an input layer of shape (224x224x3) - activation function for each layer is 'relu' and no of strides 1 by default.
2. Each convolutional layer is followed by Max Pooling layer of size 2x2 to reduce dimentionality to the half.
3. Then add a dropout layer to drop 20% of the nodes used in training to reduce the overfitting.
4. After that, The GlableAveragePooling is used for pooling the features.
5. The last layer is the dense layer with 133 nodes as the number of categories to classify and with a softmax activation function.
<p align="center">
<img src='images/sample_cnn.png' width="500" height="260" />
</p>

The other model built upon <a target='_blank' href='https://arxiv.org/pdf/1512.03385.pdf'>Resnet50</a> as following:
1. Removing the last fully connected layers from Resnet50
2. GlobalAveragePooling2D is added for pooling the features.
3. Dropout layer is added to prevent overfitting
4. Dense layer is add with 133 nodes and softmax activation function for classification

### Conclusion:

The solution works well in most cases where the image is clean but when there is some other details in the images, it needs more augmentation.

<p align="center">
<img src='resulted_images/curly_coated.png' width="500" height="260" />
</p>
<p align="center">
<img src='resulted_images/labrador_retriever.png' width="500" height="260" />
</p>
<p align="center">
<img src='resulted_images/human.png' width="500" height="260" />
</p>

