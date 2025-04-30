🔐 ActionRecognitionSystem
This project is a real-time anomaly detection system built for security surveillance. It uses deep learning techniques to detect suspicious or violent activities from videos using spatial and temporal feature modeling. The project is implemented in Python and powered by InceptionV3 and LSTM.

🧠 Project Workflow
🔁 1. Frame Extraction
Videos are broken into frames using OpenCV.

Each video is divided into multiple clips of fixed-length sequences (e.g., 20 frames).

✂️ 2. Clip Trimming & Labeling
Each clip is labeled based on the folder it belongs to (e.g., "Abuse", "Fighting", "Normal").

Clips are trimmed to a fixed frame count and normalized.

⚖️ 3. Data Balancing
The number of "Normal" clips is downsampled to match anomalous clip counts.

This prevents the model from becoming biased.

🧬 4. Spatial Feature Extraction
InceptionV3 (pretrained on ImageNet) is used to extract frame-level features.

This reduces input size and focuses on meaningful spatial representations.

⏳ 5. Temporal Modeling
LSTM is applied on sequences of frame features to learn motion patterns.

Helps distinguish between normal and anomalous sequences over time.

🏋️ 6. Training
LSTM model is trained on the extracted features.

Model is evaluated using validation set and saved to disk.

🔎 7. Inference
Clips from new test videos are processed the same way.

The trained LSTM model classifies each clip.

Output includes predicted label, inference time, and clip count.

🔍 Technologies Used
Python

TensorFlow / Keras

OpenCV

Pretrained InceptionV3

LSTM (Long Short-Term Memory)

Numpy


1. Dataset
    Link: https://drive.google.com/drive/folders/10uzJBLYEAH-u7rA2nqJzhRa-nuJwnmNU?usp=sharing
   
🏋️ 2. python training.py
Extracts frames and features

Trains and saves the LSTM model

🔎 3. Run Inference
bash
Copy
Edit
python testing.py



🧠 Why These Models?
InceptionV3 is used to extract high-level semantic features from each frame using transfer learning.

LSTM is used because it can model temporal sequences, making it suitable for video anomaly detection where time and motion matter.

💡 Future Enhancements
Integrate a real-time video stream (CCTV feed)

Use 3D CNNs or Transformer-based models for better spatio-temporal learning

Add a UI with live alerts for suspicious activity

Train on more diverse datasets (e.g., UCF Crime, ShanghaiTech)




📈 Metrics
During testing, the system outputs:

Inference time per video

Number of clips processed

Predicted class per clip

Additional metrics like confusion matrix, accuracy, and precision can be integrated later.

🧪 Preprocessing Overview
Frame extraction at consistent intervals

Trimming to 20 frames per clip

Labeling from folder name

Downsampling normal data

Feature extraction with InceptionV3

🧠 Key Concepts
Spatial Modeling: CNNs extract visual context from each frame.

Temporal Modeling: LSTM understands how motion evolves over time.

Transfer Learning: Leverage pre-trained CNNs to reduce training time and improve performance.

🗂️ Dataset (Example)
Train and Test folders contain 14 classes from UCF-Crime (or custom-labeled folders like "Abuse", "Fighting", "Normal").

PNG frames extracted from each video.

Approximately 20 frames per clip, used as input to the LSTM.

