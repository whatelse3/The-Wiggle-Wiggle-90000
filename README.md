# The-Wiggle-Wiggle-90000
A wifi connected esp32s3 based wave maker swivel for true random flow

The Wiggle Wiggle 9000 - firmware
=================================
Aquarium wavemaker: 1 to 4 servos ("wiggles") on a PCA9685, driven by a
Seeed XIAO ESP32S3, with a web interface.

Requirements
- Arduino IDE (or arduino-cli) with the "esp32" board package by Espressif,
  version 3.3.x. Board: XIAO_ESP32S3.
- Libraries (via the Library Manager):
  - WiFiManager 2.0.17 (tzapu)
  - ArduinoJson 7.4.x
  - Adafruit PWM Servo Driver Library 3.0.x (installs Adafruit BusIO too)

Wiring
- PCA9685: SDA -> D4, SCL -> D5, VCC -> 3V3, GND -> GND.
  V+ is the power supply for the servos and does not connect to the XIAO.
- Servos on channels 0 to 3 of the PCA9685.
- LED strips (optional, WS2812B, 12 LEDs per strip): data on D0 to D3
  for wiggles 1 to 4, with GND shared with the XIAO.

First time
- Keep both files (.ino and .h) together in the folder "wiggle_wiggle_9000"
  and upload that folder to the XIAO.
- Connect to the WiFi network "Wiggle Wiggle 9000 - Unit 1" and choose your
  own network there.
- After that it can be reached at http://wigglewiggle9000.local
- In Settings -> Servos, first choose your servo type (angle range, pulse
  widths), then set the center and limits of each wiggle with the sliders.

Updating
- Upload the new version the same way. Everything is kept: programs,
  schedule, centers and limits, LED settings, unit name and WiFi. These are
  stored in a separate part of the flash that a normal upload leaves alone.
- In the Arduino IDE Tools menu, keep:
  - "Erase All Flash Before Sketch Upload" on Disabled (the default).
    Enabled erases everything, WiFi included.
  - The same board (XIAO_ESP32S3) and Partition Scheme as last time.
    A different partition scheme can lose the stored settings.
- Coming from a version without servo settings: they start as a standard
  180° servo (500-2500 µs, 50 Hz), which is exactly how those versions
  worked, so the servos behave the same. Change them in Settings -> Servos
  if you use other servos.



  Makerwold Page for 3d files:

  https://makerworld.com/nl/models/3650292-the-wiggle-wiggle-9000-for-a-true-random-flow
- Very old versions without a schedule per wiggle: WiFi is kept, but the
  programs and the schedule start from the defaults.
