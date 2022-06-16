# Classifying Album Genres based on Album Artwork with Neural Networks

Maxwell Wood

### Abstract

Herein I use a convolutional neural network to classify an album's genre based solely on its album artwork. I compare how a model trained from scratch performs to a model that leverages transfer learning and find transfer learning significantly improves my models accuracy prediction. 

### Design

The goal of this project was to build a neural network model that classified album genre's from album artwork. The genre labels for the albums were based on if the  album had appeared on one of the billboard album genre charts from 2004 until present and included Rock, Rap, Country, Jazz, Holiday, and Latin. Any album that appeared on more than one chart was removed from all chart lists so that each group was purely representative of its genre. I choose these genres because they had the least overlap with eachother. For example Billboards "alternative" album and its "hip-hop R&B" charts weren't scraped due to significant overlap with the rock and rap charts respectively. I started looking at a binary classification models that could classify one genre from another and then moved on to building a model that could classify an album into one of the 6 genres. For the 6 genre classifier I split data into a train/validate/test dataset and then started with a CNN built from scratch. After training this model I moved on to using transfer learning from mobilnet v2 with the base models parameters frozen. Then, after training the model for 20 epochs I unfroze the base model and allowed for training to occur for 10 epochs. I found that unfreezing the base model allowed for significant overfitting of the training data compared to the validation data and decided to use the model where the base parameters remained frozen to score my model on the test dataset. 

### Data 

The dataset used here was created using billboard.py and Spotipy along with Spotify's api. I used billboard.py to get a list of albums/artists that had appeared on their Rock, Rap, Country, Jazz, Holiday, and Latin album charts since 2004 and then used Spotipy to download the album artwork to be used for training the model. In total I scraped over 8.2 thousand albums to train the model on. 

### Algorithms

* Modeling 
  * Tried CNN changing different layers
  * Then tried transfer learning with Mobile Net with the base model both frozen and unfrozen
* Visualizing
  * Matplotlib

### Tools

	* Keras/Tensorflow for modeling
	* Numpy, Pandas for EDA
	* Billboard.py and spotipy for gathering data