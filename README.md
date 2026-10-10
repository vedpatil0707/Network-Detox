# Network Detox: Offline Tree Identification 🌳

Network Detox is an offline-first mobile application built with Flutter that enables users to identify tree species using on-device Machine Learning (CNN) and converse about them via an embedded Large Language Model (LLM).

## Features

* **Offline CNN Tree Identification**: Instantly identify tree species in real-time without an internet connection using a quantized local TFLite model.
* **Offline LLM Question Answering**: Have interactive, contextual conversations about identified trees powered by a local Llama.cpp GGUF model running entirely on your device.
* **Camera Scanning**: Directly capture images of leaves, bark, or entire trees for classification.
* **QR Scanning**: Quickly look up specific trees in botanical gardens or parks using integrated QR code support.

## Technology Stack

* **Frontend**: Flutter / Dart
* **Machine Learning**: TensorFlow Lite (CNN)
* **Local AI**: Llama.cpp (LLM)
* **Database**: Local JSON Knowledge Graph

## Requirements

* **Flutter Version**: >= 3.41.6
* **Android SDK**: Min SDK 26, Target SDK 34+
* **Disk Space**: ~2GB free space for the offline LLM model.

## Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/network_detox.git
   cd network_detox
   ```

2. **Install Dependencies**
   Run the following command to download Flutter dependencies. This will automatically regenerate the `.dart_tool` and `android/local.properties` specific to your local SDKs.
   ```bash
   flutter pub get
   ```

3. **Install LLM Model (Optional for full features)**
   The CNN model (`model_quantized.tflite`) is already bundled in the `assets/ml/` folder. However, for the conversational agent, you must provide a `.gguf` model (e.g., Qwen2.5-1.5B).
   * Place your downloaded `.gguf` model into the designated models folder (or use the built-in model download manager).

## Build Instructions

To build a release APK for Android:

```bash
flutter build apk --release
```

To run on a connected physical device:

```bash
flutter run --release
```
*(Note: Release mode is strongly recommended for testing inference speed, as debug mode incurs heavy performance penalties for local AI).*

## Demo Usage

1. **Scan a Tree**: Launch the app and tap "Camera" to identify a tree, or "QR" to scan a tree tag.
2. **View Results**: The offline CNN will classify the tree and load its profile from the local `tree_registry.json`.
3. **Ask AI**: Tap the "Ask" button to launch the chat interface and ask specific questions about the tree (e.g., "What are its medicinal uses?"). The local LLM will stream the answer without requiring an internet connection.

## Future Work

* Expand CNN dataset to cover 500+ species.
* Explore Vulkan GPU acceleration for the LLM on supported Android devices.
* iOS CoreML and Metal acceleration support.
