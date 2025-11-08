# **Tone Control Board – Complete Project Documentation**

## 1. **Project Overview**

This project implements a **Hi-Fi audio tone-control preamplifier board** designed to provide adjustable **bass and treble equalization** for stereo audio systems. The circuit is based on the **Baxandall tone-control topology**, which offers smooth and natural frequency response shaping with minimal distortion.

The design uses a **quad operational amplifier (LM324)** to amplify and process stereo audio:
Left (L) and Right (R) channels each have independent **Bass** and **Treble** adjustment networks.

The compact PCB integrates passive RC shaping networks, gain stage, input filtering, and output buffering—making it easily integrable with any audio amplifier, home-theater system, or DIY Hi-Fi design.
<img width="794" height="377" alt="image" src="https://github.com/user-attachments/assets/8b20a388-ec21-4850-b27c-bb0a66d735cf" />
<img width="827" height="411" alt="image" src="https://github.com/user-attachments/assets/011d7840-b0c1-47b4-8de2-3f1fa66ebf65" />

---

## 2. **Key Features**

* Stereo tone-control module (Baxandall architecture)
* Independent bass and treble adjustment
* Smooth EQ curves with minimal harmonic distortion
* Input / output AC-coupling to block DC
* Single-supply operation supported
* LM324 quad op-amp
* Low noise design
* Compact PCB layout
* Ready for integration with:

  * Pre-amps
  * Power amplifiers
  * Home theater
  * Speakers

---

## 3. **Applications**

* Hi-Fi preamplifiers
* Home-theatre systems
* DIY audio amplifiers
* Bass/treble equalization
* Speaker tone shaping
* Studio tone-dressing

---

## 4. **Expanded Theory of Operation**

This Tone Control board uses the **Baxandall active tone control** circuit.
A Baxandall network provides symmetrical boost/cut of bass and treble frequencies using op-amp active filtering. The amplifier’s high input impedance and controlled gain maintain strong frequency linearity.

### 4.1 Audio Path

Each stereo channel (L + R) is processed independently:

```
Audio Input → Buffer → Baxandall EQ → Output
```

### 4.2 Bass Control Section

A variable potentiometer adjusts low-frequency tones (≈ 20 Hz–300 Hz).
Bass boost/cut is achieved by altering the low-frequency feedback path.

### 4.3 Treble Control Section

A second potentiometer alters high-frequency tones (≈ 4 kHz–20 kHz).
EQ adjustment changes the small-signal HF feedback path shaping.

### 4.4 Operational Amplifier — LM324

LM324 contains four op-amps per IC:

* Two channels for the **Left-channel tone network**
* Two channels for the **Right-channel tone network**

It provides:

* Low supply operation (3–32 V)
* Good gain bandwidth for tone control
* Low quiescent current

---

## 5. **System Block Diagram**

```
  L_IN → Buffer → Baxandall EQ → L_OUT
  R_IN → Buffer → Baxandall EQ → R_OUT
```

Internally:

```
            Bass Pot
Audio → Amp -----------→ Output
             Treble Pot
```

---

## 6. **Hardware Architecture**

| Block               | Description               |
| ------------------- | ------------------------- |
| Input coupling      | Removes DC from source    |
| Buffer stage        | Increases input impedance |
| Baxandall network   | Bass + treble shaping     |
| Output buffers      | Low output impedance      |
| Potentiometers      | User frequency control    |
| Passive RC networks | Tone shaping              |
| LM324 op-amp        | Active EQ core            |

---

## 7. **Component Specifications**

### ✅ **LM324 — Quad Op-Amp**

| Parameter         | Value                  |
| ----------------- | ---------------------- |
| Supply voltage    | 3–32 V (single-supply) |
| Output            | Rail-to-ground         |
| No. of amplifiers | 4                      |
| Slew rate         | 0.5 V/μs               |
| Gain bandwidth    | 1 MHz                  |
| Input bias        | 20 nA                  |

Function:
Amplifies and processes EQ network signals.

---

### ✅ **Potentiometers**

| Ref | Value  | Function     |
| --- | ------ | ------------ |
| RP1 | 100 kΩ | Left treble  |
| RP2 | 100 kΩ | Left bass    |
| RP3 | 100 kΩ | Right treble |
| RP4 | 100 kΩ | Right bass   |

---

### ✅ Selected Capacitors

| Component | Value  | Function         |
| --------- | ------ | ---------------- |
| C7 / C12  | 22 nF  | HF shaping       |
| C8 / C13  | 220 nF | LF shaping       |
| C9 / C14  | 2.2 nF | HF shaping       |
| C10/ C15  | 22 nF  | HF shaping       |
| C11/ C16  | 10 µF  | EQ coupling      |
| C17/ C18  | 47 µF  | Power decoupling |

---

### ✅ Resistor Network

Typical values:

* 4.7 kΩ
* 10 kΩ
* 12 kΩ
* 100 kΩ

Function:
Frequency response definition and op-amp biasing.

---

## 8. **Electrical Specifications**

| Parameter        | Specification                |
| ---------------- | ---------------------------- |
| Supply voltage   | 9–24 V DC                    |
| Channels         | 2 (stereo)                   |
| Bass range       | ≈ 20–300 Hz                  |
| Treble range     | ≈ 4–20 kHz                   |
| Gain             | Near unity (can be adjusted) |
| THD              | Low (LM324 controlled)       |
| Input impedance  | High                         |
| Output impedance | Low                          |

---

## 9. **Installation & Usage Guide**

### 9.1 Requirements

| Item         | Notes                 |
| ------------ | --------------------- |
| Power Supply | 9–24 V                |
| Audio Source | Line-level            |
| Load         | Audio amplifier input |

---

### 9.2 Setup

1. Connect **L/R input** audio signals
2. Connect **L/R outputs** to power amplifier
3. Power board from clean DC supply
4. Adjust knobs:

   * Bass
   * Treble

---

## 10. **PCB Features**

* Isolated left/right networks
* Separate RC shaping per channel
* Onboard op-amp
* Clear silkscreen labeling
* Decoupled supply rails
* Compact layout
* Designed for low noise
* Through-hole pots for easy mounting

---

## 11. **Bill of Materials (BOM)**

| Item |  Qty | Ref               | Description                  |
| ---: | :--: | ----------------- | ---------------------------- |
|    1 |   1  | U1                | LM324 quad op-amp            |
|    2 |   4  | RP1–RP4           | 100 kΩ pots                  |
|    3 |   2  | C11, C16          | 10 µF caps                   |
|    4 |   2  | C17, C18          | 47 µF power caps             |
|    5 |   4  | C7, C10, C12, C15 | 22 nF                        |
|    6 |   2  | C8, C13           | 220 nF                       |
|    7 |   2  | C9, C14           | 2.2 nF                       |
|    8 | many | R3–R14            | 4.7 kΩ, 10 kΩ, 12 kΩ, 100 kΩ |
|    9 |   —  | —                 | PCB + connectors             |

---

## 12. **Advantages**

* Wide tone adjustment range
* Low noise
* Stereo processing
* Simple and low-cost
* Compatible with most amplifiers
* Very natural sounding response

---

## 13. **Suggested Improvements**

| Improvement          | Benefit           |
| -------------------- | ----------------- |
| Upgrade to TL074     | Lower noise       |
| Add volume control   | Full preamp       |
| Add bypass switch    | Flat mode         |
| Add midrange control | 3-band EQ         |
| Add SMD version      | Smaller footprint |

---

## 14. **Conclusion**

This Baxandall-based Tone Control Board is a **high-quality analog equalizer** designed for audio enthusiasts and DIY amplifier builders.
Its stereo implementation, LM324-based amplification, and carefully selected RC shaping networks ensure clean, controlled bass and treble response.

It can be integrated into:

* Preamplifiers
* Home-theater amplifiers
* Guitar amplifiers
* Active speakers

The board is simple, inexpensive, and highly effective—making it an excellent choice for audio-signal conditioning.

## 15. **LICENSE**
This project is an open-source project licensed under MIT OpenSource License. See the LICENSE file for more info.
