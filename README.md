# Cricket-Analysis-using-YOLOv8n
Using YOLOv8n to detect whether the batsman is right or left handed .

DESCRIPTION

This project implements a pose estimation–based video analysis pipeline to automatically detect whether a cricket batsman is right-handed or left-handed, based on their stance captured in video footage.
Using Ultralytics YOLOv8-Pose, the system processes each frame of the video, extracts pose keypoints (shoulders, hips, knees, wrists), and applies a geometric rule-based algorithm to determine the stance orientation.
This project demonstrates how sports analytics can be automated using modern deep learning–based pose estimation.

In cricket, understanding a batsman's stance is critical for tactical insights, coaching analysis, and automated tagging in video analytics systems.
However, manually annotating each player’s handedness from match footage is time-consuming and error-prone.

This project solves the problem of automatically classifying the batsman’s stance (Right vs. Left) by analyzing the relative horizontal positions of their body keypoints (shoulders and knees) extracted from each frame.

Pose Estimation:
YOLOv8-Pose detects the batsman and returns 17 keypoints (COCO format).

Keypoint Extraction:
The x-coordinates of the left/right shoulders (indices 5, 6) and left/right knees (indices 11, 12) are extracted.

Geometric Rule:
The stance is determined by comparing the relative horizontal positions:
delta_s = right_shoulder_x - left_shoulder_x
delta_k = right_knee_x - left_knee_x

if delta_s < 0 and delta_k < 0:
    stance = "Right-Handed"
elif delta_s > 0 and delta_k > 0:
    stance = "Left-Handed"
    
Negative deltas → right-handed stance

Positive deltas → left-handed stance

OUTPUT: left or right handed batsman
