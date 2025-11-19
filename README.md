This project is a modular pipeline for lane line detection, road marking classification, and safe overtaking decision-making using computer vision and deep learning. It combines traditional image processing, perspective transformation, and YOLOv8-based road marking recognition for robust functionality across both video and image inputs.​

Overview
This repository contains Python modules for detecting and analyzing lane lines from camera images, classifying road markings, and determining whether overtaking is safe based on those markings. It uses YOLOv8 (best.pt) for line marking classification, blending classic image processing with modern neural network inference.​

Modules
main.py: Pipeline entry point. Processes videos or images, applies calibration, transforms perspective, thresholds for lane pixels, detects lane lines, and infers actionable guidance (e.g., keep straight, curve ahead). Integrates calls to other modules.​

CameraCalibration.py: Calibrates camera using chessboard images, computes camera matrix and distortion coefficients, and provides image undistortion utilities.​

Thresholding.py: Extracts relevant lane pixels using HLS and HSV thresholding, supports both relative and absolute thresholds.​

PerspectiveTransformation.py: Transforms images between front view and bird's-eye view for more reliable lane detection, using user-defined source and destination coordinates.​

LaneLines.py: Implements lane finding with windowing, polynomial fitting, curvature computation, and visualization. Indicates lane geometry and vehicle position relative to center. Can visualize recommended steering actions.​

YOLOv8 Integration
The repository expects a YOLOv8 model file (best.pt) to be present for detecting and classifying road markings such as solid lane lines, dashed lines, and special symbols.

Classification results are used to determine overtaking safety. For example, solid lines will trigger a "no overtaking" warning, whereas dashed lines may permit overtaking.

Ensure you install required YOLOv8 and associated Python packages before using this feature.

How it Works
Calibration is performed with chessboard images to correct lens distortion before processing.​

Perspective transformation allows robust lane geometry extraction.​

Thresholding and lane modeling extract lane structure, curvature, and vehicle deviation.​

YOLOv8 detects specific line markings, interpreting overtaking safety scenarios using image classification results.

Outputs
Processed videos/images with overlays showing detected lanes and safe/unsafe overtaking indications.

Curvature and vehicle deviation info annotated on outputs.

Action guidance (keep straight, left/right curve, overtaking permitted/forbidden).

Customization
Tweak source/destination points in PerspectiveTransformation.py for different camera setups.

Retrain YOLOv8 for local road marking types and replace best.pt.
