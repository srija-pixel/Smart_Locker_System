# 🔐 Smart Locker System

A secure and intelligent locker system built using **ESP32, ESP32-CAM, Python, Flask, and Telegram**. The system combines physical access control, OTP-based authentication, and image capture to provide a smart and monitored locker solution.

---

## 📌 Overview

The Smart Locker System is designed to provide secure access to a physical locker using a combination of:

- 🔢 OTP-based authentication
- 📷 ESP32-CAM image capture
- 📱 Telegram notifications
- 🌐 ESP32-based control
- 🐍 Python Flask backend
- 🔒 Secure credential management

When a user attempts to access the locker, the system can generate and send an OTP, verify the authentication request, capture an image, and send the captured image through Telegram.

---

## ✨ Features

- 🔐 **OTP-Based Authentication**
  - Generates a one-time password for locker access.
  - OTP is handled through the ESP32 and backend server.

- 📷 **Image Capture**
  - ESP32-CAM captures an image during the access process.
  - Captured images are transferred to the Python server.

- 📱 **Telegram Notifications**
  - Sends OTPs and captured images through Telegram.
  - Provides remote notifications for locker activity.

- 🌐 **ESP32 Control**
  - Controls the locker hardware and communicates with the backend.

- 🖥️ **Flask Backend**
  - Handles image capture requests.
  - Communicates with the ESP32.
  - Integrates Telegram Bot API.

- 🔑 **Secure Configuration**
  - Wi-Fi credentials, IP addresses, Telegram credentials, and other private configuration values are stored locally.
  - Sensitive files are excluded from GitHub using `.gitignore`.

---

## 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │      User            │
                    │  Locker Access       │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │       ESP32          │
                    │  Locker Controller   │
                    └──────────┬───────────┘
                               │
                     OTP / HTTP Requests
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Python + Flask     │
                    │      Backend         │
                    └───────┬───────┬──────┘
                            │       │
                 Image      │       │ OTP / Message
                 Request    │       │
                            ▼       ▼
                  ┌──────────────┐ ┌──────────────┐
                  │ ESP32-CAM    │ │   Telegram   │
                  │    Camera    │ │     Bot      │
                  └──────────────┘ └──────────────┘
                            │
                            ▼
                    Captured Image
