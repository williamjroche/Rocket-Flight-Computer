# Zeus Flight Computer

Custom flight computer for amature rockets, code named Zeus. This FC records flight data, detects apogee using a 9-axis IMU + baraomter sensor, has a built in pyro circut for firing e-matches (parachute, stage seperation, etc.).

## Project Status

- PCB design in the works, based on my Atlas Flight Controller from this project: https://github.com/williamjroche/Autonomous_drone
- Prototyping in progress on protoboard
- Board not yet fabricated, working on completing prototype first to test architecture

## Features

- 3 pyro channels with continuity sensing
- IMU + barometer sensors for apogee detection
- microSD card reader for data logging
- Automatic USB / external battery power switching (using PMOS switching circuit)
- MicroPython firmware (adapted from drone flight controller project)

## Hardware Overview

- Check out my system diagrams: [System Drawings](./System%20Drawings)
    - Explains architecture at a top level overview
- Key components table (MCU, IMU, barometer, flash, SD, pyro MOSFETs, power management)
- Link to schematic/PCB files [Zeus_FC_PCB](./Zeus_FC_PCB)

## PCB

<img width="1396" height="907" alt="image" src="https://github.com/user-attachments/assets/47f5aabe-4733-4167-9e65-f5c129103ef9" />

- Stackup summary (4-layer: signal / GND / 3.3V / signal)
- Check out other photos [PCB Photos](./PCB%20Photos)
- Note: working on finding smaller SMD type IRFZ44N mosfets because these are ugly

## Protoboard Prototype

- Purpose: validate firmware and circuit behavior ahead of PCB fabrication
- Hardware used (Pico 2W, IMU breakout (ICM-20948), barometer breakout (BPM 384), microSD breakout, custom designed and fabricated 12v to 3.3v regulator board)
- Photos coming soon

## Firmware

- project specific firmware not yet developed, coming soon
- Firmware will be based off of Atlas FC firmware: https://github.com/williamjroche/Autonomous_drone/tree/main/flight_controller

## Wiring / Pinout

- Micro SD card reader:
  - CS – GPIO8
  - MISO – GPIO16
  - SCK – GPIO18
  - MOSI – GPIO19
- IMU Board:
  - SDA – GPIO0
  - SCL – GPIO1
- Barometer:
  - SDA: GPIO20
  - SCL: GPIO21

## Getting Started / Prototype Setup

If you want to make your own prototype, you'll need the following materials:

- protoboard, decently sized (mine is 7cm x 9cm)
- soldering iron
- solder (I recommend lead free)
- Fume extractor
- something to clean the soldering iron tip, like steel wool)
- 22awg wire
- Toggle switches (2)
- 1 3s LiPO battery
- Something to convert the 11.1v LiPO battery to 3.3v for the Pi
    - A buck converter off amazon will work
    - or you can download the files from the device I built from here: (https://github.com/williamjroche/Autonomous_drone/tree/main/dual_power_supply)
        - Can be fabricated using PCBway, JLCPCB, or any of your favorite fabricators. I ordered from PCBway.
- Raspberry Pi Pico 2W
- ICM-20948 IMU breakout
- BPM 384 barometer breakout
- Any microSD card reader breakout
- Electrical tape or hot glue
- MicroSD card
- Flux to make soldering easier
- Multimeter to test electrical connections (not needed but helpful)

## My Prototype: 

<img width="5712" height="4284" alt="IMG_6008" src="https://github.com/user-attachments/assets/29b842ca-36bf-4949-b291-587b7689d91e" />

Here is a demo video of the working prototype: https://youtube.com/shorts/D4aav9IAWUg?si=ib71gM45oc4MuGbN

At the moment only the IMU is programmed, I need to work on the barometer sensor and apogee detection + saving data to micro SD card. You can see in the video I am using my custom dual power PCB I designed which is converting the 12v from the battery to a usable 3.3v for our sensors and Pico 2W. The switch you see is me prototyping a power switch.

## Safety Notes

- Be careful handling pyro charges!
      - I am not responible for any accidents.

## Acknowledgments

- Link to drone flight controller project: https://github.com/williamjroche/Autonomous_drone/tree/main
    - Dual Power Supply PCB is the 12v to 3.3v converter I am using on this project. The explaination under this other repo readme will help clear up any   confusion.
