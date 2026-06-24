# STM32 Stopwatch

A 0–99 second stopwatch built on the **STM32F103C8T6** (Blue Pill) using STM32CubeIDE and the HAL library.

## Features

- **Dual 7-segment display** (common anode) showing seconds from 00 to 99
- **Start / Pause / Resume** — single button toggle (PB12)
- **Reset** — dedicated reset button (PB13), clears counter back to 00
- **Auto-stop at 99** — counter stops and the on-board LED (PC13) lights up
- **Timer interrupt driven** — TIM2 generates a 1-second tick via interrupt (Prescaler 3200-1, Period 10000-1 @ 32 MHz SYSCLK)

## Hardware

| Component | Pin(s) |
|---|---|
| 7-Seg Tens digit (A–G) | PA0 – PA6 |
| 7-Seg Units digit (A–G) | PB0, PB1, PB7, PB3 – PB6 |
| Start/Pause button | PB12 (internal pull-up, active LOW) |
| Reset button | PB13 (internal pull-up, active LOW) |
| On-board LED | PC13 (active LOW) |

## How It Works

1. On power-up the display shows **00** and the stopwatch is paused.
2. Press the **Start** button (PB12) to begin counting.
3. Press **PB12** again to **pause**; press once more to **resume**.
4. When the counter reaches **99**, counting stops automatically and the PC13 LED turns ON.
5. Press the **Reset** button (PB13) at any time to return to **00** and turn the LED OFF.

## Building & Flashing

1. Open the project in **STM32CubeIDE** (File → Import → Existing Projects into Workspace).
2. Build the project (Project → Build All or Ctrl+B).
3. Flash to the board via ST-LINK (Run → Debug or Run → Run).

## Demo Video

> _Demo video will be added here._

## Project Structure

```
stopwatch/
├── Core/
│   ├── Inc/          # Header files
│   ├── Src/          # Source files (main.c, interrupts, etc.)
│   └── Startup/      # Startup assembly
├── Drivers/          # STM32 HAL & CMSIS drivers
├── stopwatch.ioc     # STM32CubeMX configuration
└── STM32F103C8TX_FLASH.ld  # Linker script
```
