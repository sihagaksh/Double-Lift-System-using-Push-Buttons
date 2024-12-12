# Dual Lift System with Push Buttons

## Overview

This project simulates a **dual-lift system** controlled by an **Arduino**, designed to prioritize lift allocation, handle emergency situations, and include floor-specific delay times. The system uses a **LiquidCrystal_I2C LCD** to display real-time status, and features buttons for six floors and an emergency stop. Powered by an **L298 motor driver**, the lifts' movements are simulated with pre-defined delay times to mimic realistic travel between floors.

## Features

### 1. **Dual-Lift System**
- Two lifts available to fulfill floor requests.
- Lift allocation prioritizes the closest lift or Lift 1 in case of a tie.

### 2. **LCD Display**
- Real-time updates of current floor positions and lift movements.

### 3. **Emergency Mode**
- Emergency button brings both lifts to Floor 1 immediately, overriding other operations.

### 4. **Six-Floor Control**
- Buttons allow requests for any floor from 1 to 6.

### 5. **Optimized Lift Movement**
- Pre-defined delay times simulate realistic travel durations between floors.
- The system calculates and selects the optimal lift for each request.

## Hardware Components

- **Arduino UNO**
- **LiquidCrystal_I2C LCD (16x2)**
- **L298 Motor Driver**
- **Buttons:**
  - 6 floor request buttons (connected to digital pins 2–7).
  - 1 emergency button (connected to analog pin A0).
- **DC Motors** for lift movement (connected via motor driver).
- **Power Supply** for external motor power.

## Pin Configuration

### Lift 1:
- **Motor Control Pins:**
  - IN1: Pin 9
  - IN2: Pin 8
  - Enable Pin: Pin 10

### Lift 2:
- **Motor Control Pins:**
  - IN3: Pin 12
  - IN4: Pin 13
  - Enable Pin: Pin 11

### Floor Buttons:
- **Floor 1:** Pin 7
- **Floor 2:** Pin 6
- **Floor 3:** Pin 5
- **Floor 4:** Pin 4
- **Floor 5:** Pin 3
- **Floor 6:** Pin 2

### Emergency Button:
- **Pin:** A0

## Setup Instructions

### 1. Hardware Setup:
- Connect DC motors to the L298 motor driver.
- Connect floor and emergency buttons to the specified pins.
- Attach the LiquidCrystal_I2C LCD to the Arduino (I2C address: 0x27).

### 2. Code Upload:
- Open the Arduino IDE and upload the provided code to the Arduino UNO.

### 3. Power Supply:
- Connect the Arduino to a 5V USB power source.
- Ensure the motor driver is powered by an appropriate external source.

## Operating Instructions

### 1. Initialization:
- On power-up, the LCD will display:
  
Both lifts start at **Floor 1**.

### 2. Floor Requests:
- Press any floor button (1–6) to call a lift to the desired floor.
- The LCD will display the request and indicate which lift is moving.

### 3. Emergency Stop:
- Press the emergency button to activate emergency mode.
- Both lifts will immediately move to **Floor 1**, overriding all other operations.
- The LCD will display:


### 4. Resume Operation:
- After the emergency is resolved, the system resets and resumes normal operation.

## Example Scenarios

### 1. Request Floor 3:
- If **Lift 1** is on Floor 1 and **Lift 2** is on Floor 4:
- Lift 1 will move to Floor 3 (closer lift).
- The LCD will display:
  
  ```
  FLOOR REQ: 3
  L1 MOVING...
  ```

### 2. Emergency Activation:
- Both lifts, regardless of their current floors, move to Floor 1.
- The LCD will display:


## Customization

### 1. Delay Times:
- Modify the `delayLift1` and `delayLift2` matrices for different travel durations.

### 2. Motor Speed:
- Adjust the `motorSpeed` constant (0–255) for faster or slower movement.

### 3. Floor Count:
- Expand or reduce the number of floors by adjusting button pins and delay arrays.

## Troubleshooting

### 1. LCD Not Displaying:
- Ensure the I2C address matches your LCD module.
- Confirm proper connections for SDA and SCL pins.

### 2. Lift Not Moving:
- Check motor driver connections and external power.
- Verify the motor pins are correctly defined in the code.

### 3. Emergency Mode Fails:
- Confirm the emergency button is connected to pin A0.
- Test the button functionality with a simple input reading sketch.

---

Enjoy using your **Arduino-powered dual-lift system**!

