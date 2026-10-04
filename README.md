# HyperOS Bootloader Sniper 🎯

An ultra-fast, zero-dependency Windows batch script (.bat) designed to automatically bypass the countdown and capture bootloader unlock slots in the Xiaomi Community app. Optimized specifically for HyperOS 1, HyperOS 2, and HyperOS 3 layouts across all Redmi, POCO, and Xiaomi devices.

The script targets exactly 00:00:00 Beijing Time (UTC/GMT +8) when Xiaomi resets its daily limits.

## ✨ Features

- 🎯 Universal Screen Awareness: No hardcoded layout grids. The script automatically reads your device's physical resolution via ADB and calculates the exact button coordinates using a golden precision matrix (X=50%, Y=90.83%). Works flawlessly on HD+, Full HD+, 1.5K, and 2K screens.
- 🌍 Global Timezone Engine: Automatically asks for your computer's UTC/GMT offset, converts Beijing midnight to your precise local computer time, and stands on guard.
- ⚡️ One-Shot Pipeline Spam: Standard loops re-initialize adb.exe every single click, losing up to 200ms per tap. This script pre-compiles all 45 taps into a single unified shell command string, executing an instantaneous, atomic volley of clicks directly into the Android input pipe.
- 🪶 100% Native & Clean: Built completely on native Windows Batch command logic. Zero third-party software, zero compilation errors, and strictly no character-encoding memory leaks.

## 🚀 How to Use

### 1. Prerequisites
- ADB Drivers: Ensure adb.exe is installed on your Windows PC and added to your System PATH environment.
- Device Prep: Enable USB Debugging inside the Developer Options on your Xiaomi/POCO/Redmi phone.
- Target Page: Open the Xiaomi Community App, navigate to the Bootloader Unlocking page, and stop right before the application screen where the Apply for unlocking button sits.

### 2. Execution
1. Connect your smartphone to the PC via a USB cable.
2. Run hyperos_sniper.bat (Run as Administrator is recommended to avoid permission delays).
3. The script will automatically detect your ADB Device ID, fetch your real device name, and calculate your target display coordinates.
4. Select your computer's current UTC/GMT timezone from the interactive menu.
5. Keep the window open. Exactly 1 second before midnight in Beijing, the script will trigger an unyielding tap storm.

## ⚙️ How It Works Under the Hood

The script avoids high-overhead system tools inside the time loop. Instead, it natively queries the volatile %TIME% Windows clock state registers on a nanosecond loop interval, bypassing standard execution freezes:

:loop
set "current_time=%TIME%"
if "%current_time:~0,8%"=="%LOCAL_TARGET%" goto attack
goto loop
Once triggered, it passes a concatenated stack string (input tap X Y && input tap X Y...) down the active ADB socket bridge, dumping the tap sequence inside the device runtime memory without Windows process overhead.

## ⚖️ License
This project is licensed under the MIT License - feel free to use, modify, and star the repo if it saved your slot!
