# Privacy Policy for Veras: Polygraph and lie detector

**Last Updated: August 26, 2026**

This Privacy Policy governs the data processing practices of the mobile application **"Veras: Polygraph and lie detector"** (hereinafter referred to as the "Application"). 

Our primary guiding principle is absolute data privacy and security. The Application is designed as a **100% offline, standalone security and analytical tool**. It does not collect, transmit, share, or store any user data on external servers. All operations are executed entirely on your local device.

---

## 1. Information Collection and Use

To provide accurate psycho-physiological analysis and verification, the Application requires access to specific hardware sensors. This data is processed in real-time using local algorithms and native C++ modules.

### a. Audio Data (Microphone)
* **Purpose:** Required to capture vocal responses during sessions. The local Digital Signal Processing (DSP) engine analyzes audio samples using Discrete Fourier Transform (DFT) algorithms to measure micro-tremors in the human voice (8–14 Hz spectrum).
* **Storage:** Recorded audio is encoded into an AAC/MPEG-4 container and stored directly inside the application's isolated local database as private binary data (BLOB). It is never sent over the network.

### b. Kinetic Data (Device Accelerometer)
* **Purpose:** Used to detect physical micro-vibrations and physiological hand tremors when the subject holds the device. The data is processed locally via a high-pass filter to isolate vegetative stress indicators from gravity and deliberate movements.
* **Storage:** Extracted numerical sensor values are logged locally alongside timestamps in the isolated database.

### c. Touch and Pressure Data (Display Touch Sensor)
* **Purpose:** Used to implement the "Touch-and-Hold" response mechanism. The Application measures the surface contact area and micro-variations in display touch metrics to evaluate touch dynamics and muscle tension during vocal responses.
* **Storage:** Numerical metrics are stored strictly on the local device.

---

## 2. On-Device Data Storage and Security

The Application implements strict information security (InfoSec) protocols to prevent data leaks and unauthorized modifications:

* **No Cloud Connection:** The Application lacks any network permissions (`android.permission.INTERNET` is not requested or utilized). It is physically impossible for the Application to leak data online.
* **Isolated Database:** All session metadata, numerical logs, and audio containers are stored inside a local SQLite database utilizing Write-Ahead Logging (WAL) and protected by Android's internal application sandbox.
* **Temporary Cache Protection:** During the expert analysis phase, required multimedia streams are briefly extracted into the application's private, encrypted external cache directory (`getExternalCacheDir()`). This directory is strictly inaccessible to standard system media players, galleries, or third-party applications.
* **Data Erasure:** Upon closing the analysis screen or utilizing the "Cascade Delete" feature on the main archive, all corresponding SQLite entries, binary logs, and temporary cache files are instantly and permanently wiped from the physical disk drive.
* **Cryptographic Integrity:** At the end of each session, a cryptographic SHA-256 digital signature (hash passport) is generated across all recorded logs. This ensures non-repudiation and blocks any unauthorized post-factum tamper tampering with the historical files.

---

## 3. Third-Party Libraries and Permissions

The Application utilizes standard, official, and open-source Google Jetpack components:
* **androidx.camera (CameraX):** Used strictly in `Preview` mode on the user's screen during open instrumental polygraphy to visually monitor micro-expressions. No video frames are recorded to disk or sent anywhere.
* **Google Gson:** Used strictly for offline local object mapping and serialization within the local database architecture.
* **No Third-Party SDKs:** The Application does not contain any analytical trackers (like Firebase Analytics, Flurry, etc.), advertisement frameworks, or cloud backend integrations.

---

## 4. Children's Privacy

The Application is intended for professional cybersecurity, human resources (HR), and analytical profiling investigations. We do not knowingly collect or log any personal data from anyone, including children under the age of 13.

---

## 5. Compliance with Global Privacy Regulations

Because **"Veras: Polygraph and lie detector"** processes all information strictly on the user's local hardware without data collection or network transmissions, it is inherently compliant with major global privacy standards, including:
* **GDPR** (General Data Protection Regulation)
* **CCPA** (California Consumer Privacy Act)
* **Google Play Developer Policies** regarding sensitive hardware permissions (Microphone, Camera).

The absolute control over the data remains entirely in the hands of the device owner/operator.

---

## 6. Changes to this Privacy Policy

We may update our Privacy Policy from time to time to reflect hardware optimizations or code adjustments. Any changes will be posted directly on this GitHub repository page with an updated modification date.

## 7. Contact Information

If you have any questions or technical inquiries regarding the data security architecture of this offline application, please open an issue in this GitHub repository or contact the developer directly.
