# Image-Description-Generation
# Basic phases of generating captions
-----------------------------------------------------------------------------------------------------------------------------
# Data Collection and Reading data
For the image description generator, Kaggle's Flickr30K dataset is used.The Flickr30k dataset contains about 30000 images each with 5 captions.

# Data Loading and Tokenization
When loading the training and testing sets, two essential tokens are included in each caption:

**'startseq**': This token signifies the beginning of every caption, providing a clear start point for the model to generate text.
**'endseq'**: This token marks the end of every caption, allowing the model to know when a caption is complete.

# Image Processing
The images sourced from the Flickr_8k dataset undergo a transformation into arrays before being fed into the ResNet 50 model. This model extracts image features just before the last classification layer, producing an array vector of length 2048 that represents the features of each image. These image features are then paired with their corresponding images and saved in a dictionary.

# Text Processing
To convert words into fixed-size vectors, two Python dictionaries are utilized:

**word_to_index['w']**: This dictionary provides the index of a given word 'w', enabling efficient word indexing.
**index_to_word['yhat']**: Conversely, this dictionary returns the word associated with a given index 'yhat', facilitating the conversion back to human-readable text.

# Data Preparation with Generator Function
For generating descriptions of input images, a Long Short Term Memory (LSTM) process is employed. LSTM networks are particularly adept at handling sequential data like text, allowing the model to understand the context and structure of captions.

# Inferencing
The model's output is processed through a softmax function, which produces a probability distribution across all words in the vocabulary. This distribution helps the model select the next word in the sequence, predicting the most likely word based on the context provided by the image.

**A Greedy Search Algorithm** is used during inference to select words with the highest probability at each step. This method, while simple, often produces reasonably coherent and fluent sentences.

# Evaluation with BLEU Score
To assess the quality of generated captions, the BLEU Score is employed as an evaluation metric. BLEU (Bilingual Evaluation Understudy) measures the similarity between the model's predicted captions and human-generated reference captions. It provides a quantitative measure of how closely the model's outputs match human expectations, allowing for robust evaluation and comparison of different models.

# Summary
Image sent to CNN (ResNet50): Input image processed through ResNet50.
Last CNN layer removed: Classification layer is discarded.
CNN produces 2048-dimensional image vector: Features extracted from the image.
Image vector and caption sent to model: Input for the caption generation model.
Model generates probability distribution: LSTM-based model predicts word probabilities.
Word with maximum probability chosen: Greedy Search Algorithm selects next word based on highest probability.

# Requirements
1. Tensorflow
2. Anaconda
3. Python 3.7
4. Numpy
