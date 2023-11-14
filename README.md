# Monet like Image Generation
The objective of this work is to bring that style of Monet using images of artist Monet, to photos (non Monet) that are provided. The notebook follows Tensorflow's direction to use CycleGAN to meet this objective.

A GAN consists of at least two neural networks: a generator model and a discriminator model. The generator is a neural network that creates the image. This generator is trained using a discriminator. The two models will work against each other, with the generator trying to trick the discriminator, and the discriminator trying to accurately classify the real vs. generated images.

Cycle GAN's are conditional GAN that performs unpaired image to image translation. That is it captures the characteristics of one image domain (Monet style in our example) and figure out how these characteristics could be translated into another image domain (normal photos in our case)

## Data
The dataset provided by Kaggle (https://www.kaggle.com/competitions/gan-getting-started/data) contains four directories: monet_tfrec, photo_tfrec, monet_jpg, and photo_jpg. For this work, only monet_tfrec and photo_tfrec were used

Monet - 300 Monet paintings sized 256x256\
Photo - 7028 photos sized 256x256 

## Model - CycleGAN
The Cycle GAN follows pix2pix example in Tensorflow(https://www.tensorflow.org/tutorials/generative/pix2pix). Like any GAN It contains a generator and a discriminator. In this cycleGAN,
- Generator - contains a UNET architecture of Downsampling and UpSampling images so that images are restored
- Discriminator - Convolutional PatchGAN Classifier that tries to classify if each image patch is real or not real
