# Driver Drowsiness Detection
## Code implementation and Explanation
The main parts of our implementation is to detect the close eye and open eye. When a driver closes eyes for certain time period , our model creates a score and 
if the score crosses the limit , the alarm is played.

There are 3 part in our implementation
- Data processing
- Model creation and training
- Driver drowsiness detection and alarm

# Data processing
- We have downloaded MRL eye data http://mrl.cs.vsb.cz/eyedataset and stored in Data folder.
- The raw data is divided into open eyes and close eyes 
- The training set and test set is created for open eyes and close eyes with 20% in test data 

# Model creation and training
- We have used Keras InceptionV3 image classification model architecture to classify the images using the "imagenet" weights
- Two extra layers are added on the top of the base model (InceptionV3) 
  - Dense layer with 64 neurons
  - Output layer with 2 neurons and softmax fuction
- The model is trained with trained data and saved in "/models/model.h5", which is used by the drowsiness detection and alarm

# Driver drowsiness detection and alarm
- Driver drowsiness detection uses the model and creates the prediction on the given eye
- To detect the eye , we have used CascadeClassifier with haarcascade_frontalface
- CascadeClassifier detects the eye co-ordinates and passes to the model to detect if eye is close or open
- The calculate a score value of the closed eye and if it crosses the limit, the alarm is played
