# 🏋️ Forearm Movement Tracker

A real-time pose estimation and arm movement tracking application using **MediaPipe** and **OpenCV**. This project tracks left and right arm curls by analyzing elbow joint angles and counts the number of completed arm movements.

---

## 🧠 Features

- Real-time webcam-based upper-body pose detection  
- Calculates elbow angles for both arms  
- Counts arm curl repetitions for left and right arms independently  
- Color-coded angle visualization and tracking lines  

---

## 📦 Requirements

Make sure you have Python 3.7+ and the following libraries installed:

```bash
pip install opencv-python mediapipe numpy
```

---

## 📷 How It Works

1. Captures video input from webcam  
2. Uses **MediaPipe Pose** to detect body landmarks  
3. Calculates elbow angles using three landmark points (shoulder, elbow, wrist)  
4. Tracks full movement cycles based on angle thresholds:
   - Angle < 45° → Start of movement
   - Angle > 120° → End of movement (counted as one rep)
5. Visualizes joints, lines, and angle labels in real-time  

---

## 📊 Output Example

```
Left Arm - Attempts: 5
Right Arm - Attempts: 4
```

- ✅ Green lines = correct angle range during movement  
- ❌ Red lines = angle is out of range  

---

## 🛠️ Customization

You can adjust angle thresholds or add more movement detection logic in:

```python
if angle_l < 45:
    movement_in_progress_left = True
elif angle_l > 120 and movement_in_progress_left:
    total_attempts_left += 1
    movement_in_progress_left = False
```

---

## 📌 Known Issues

- Only upper body is tracked; full-body support not included  
- Accuracy may vary with lighting and camera position  
- Assumes camera is positioned directly in front of the subject  

---

## 🙌 Acknowledgements

- [MediaPipe](https://google.github.io/mediapipe/)
- [OpenCV](https://opencv.org/)

