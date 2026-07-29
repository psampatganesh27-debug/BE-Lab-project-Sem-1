# BE-Lab-project-Sem-1
# Simulation-Based Room Security and Home Automation System

A digital logic circuit designed and simulated using **NI Multisim 14.1**. This project combines a passcode-based digital security lock with an automated room appliance control system (Lighting & Air Conditioning).


## 📌 Project Overview

This project implements a two-stage digital circuit using basic logic gates:
1. **Passcode Authentication:** Validates a 3-bit user input against a preset passcode.
2. **Smart Home Automation:** Controls room appliances based on authorization, motion detection, and ambient temperature status.


## 🔥 Key Features

1. **3-Bit Digital Lock:** Uses XNOR gates to compare real-time user inputs against stored passcode bits for authentication.
2. **Access Status Indicators:**
  * 🟢 **Green LED:** Indicates correct passcode entry.
  * 🔴 **Red LED:** Indicates incorrect passcode entry.
3. **Motion-Based Lighting:** Turns on the room light (`X3`) only when access is authorized **and** motion is detected.
4. **Temperature-Triggered AC Control:** Activates the Air Conditioner (`X4`) only when access is authorized, motion is detected, **and** the temperature threshold is reached.

---

## 🛠️ Circuit Architecture & Components

### **Components Used**
* **Logic Gates:** 
  * `XNOR2` (3 units) — Bitwise comparison of passcode and inputs
  * `AND2` & `AND3` — Control logic and condition validation
  * `NOT` — Logic inversion for incorrect password detection
* **Sensors / Switches (Simulated via Interactive Digital Keys):**
  * 3-Bit Input Switches (`U1`, `U2`, `U3`)
  * 3-Bit Stored Passcode (`U4`, `U5`, `U6`)
  * Check Trigger Switch (`U14`)
  * Motion Sensor Switch (`U15`)
  * Room Temperature Sensor Switch (`U16`)
* **Output Indicators:**
  * `X1` — Green Probe LED (Correct Passcode)
  * `X2` — Red Probe LED (Incorrect Passcode)
  * `X3` — Yellow Probe LED (Light Bulb)
  * `X4` — Blue Probe LED (Air Conditioner)

---

## ⚙️ Logic Breakdown

### **1. Authentication Logic**
* Input bits ($I_1, I_2, I_3$) and Passcode bits ($P_1, P_2, P_3$) are fed into three **XNOR2** gates.
* The output of all three XNOR gates is fed into a 3-input **AND** gate (`U10`). 
* If all corresponding bits match, `U10` outputs `HIGH` (`1`).
* When the **CHECK** switch (`U14`) is activated:
  * `U12` (AND gate) triggers **Green LED (`X1`)** if the code is correct.
  * `U13` (AND gate via NOT gate `U11`) triggers **Red LED (`X2`)** if the code is incorrect.

### **2. Appliance Automation Logic**
* **Light Bulb (`X3`):** Powered via `U17` (AND gate). Requires `Correct Passcode = HIGH` **AND** `Motion Detector (U15) = HIGH`.
* **Air Conditioner (`X4`):** Powered via `U18` (3-input AND gate). Requires `Correct Passcode = HIGH` **AND** `Motion Detector (U15) = HIGH` **AND** `Room Temperature Sensor (U16) = HIGH`.

---

## 🚀 Applications

* **Smart Home Security:** Keyless entry system for homes and apartments.
* **Server Room Management:** Combined access restriction and automated climate control.
* **Energy-Efficient Commercial Spaces:** Automatic light and cooling shutdown in vacant rooms or hotel suites.

---

## 💻 Simulation Setup

1. Download and install **NI Multisim 14.1** (or compatible version).
2. Open the project file (`.ms14`).
3. Press **F5** or click the **Run Simulation** button.
4. Use spacebar / key toggles to adjust inputs, passcode bits, motion, and temperature switches to test different scenarios.
