Version 1.0 | Windows 11 x64
============================================

A lightweight, portable, read-only Windows checklist that helps verify the AMD and Windows components used for automatic game-aware CCD scheduling on dual-CCD Ryzen X3D processors, including the Ryzen 9 9950X3D.

Designed for checking fresh Windows installs, custom ISOs, and debloated Windows 11 systems without changing any system settings.

FEATURES
--------
- Clean grayscale interface.
- One-page checklist of X3D-related requirements and settings.
- Clear PRESENT, CHECK, MISSING, and VERIFY indicators.
- Click an item to view the evidence and guidance.
- Rescan any time (F5).
- Save a local text report to compare installations.
- Portable single-file EXE: no installer, PowerShell, or .NET required.
- No administrator privileges requested; no network connections.

WHAT IT CHECKS
--------------
Core Windows and AMD components:
- Windows 11 and X3D CPU identification.
- AMD 3D V-Cache Optimizer service and driver.
- AMD PPM provisioning driver and provisioning service.
- Windows AMD processor driver and Power service.
- Windows Game Mode configuration.
- Xbox Game Bar package registration / game-detection support.

Additional guidance and information:
- AMD Application Compatibility Database.
- AMD chipset software metadata.
- Balanced power plan (recommended baseline).
- BIOS and CPPC details requiring manual review.
- Game DVR / background recording settings (not required for X3D scheduling).

HOW TO USE
----------
1. Download X3D_Checker.exe.
2. Install the official AMD chipset driver package appropriate for your motherboard, then restart Windows.
3. Run the EXE and review the checklist.
4. Click any item for further details.
5. Select SAVE REPORT to export a .txt file.
6. After switching to a different Windows ISO, repeat the scan and compare reports.

READING RESULTS
---------------
PRESENT - The required component or setting was detected.
CHECK   - The detected configuration needs attention.
MISSING - The expected registration or component was not detected.
VERIFY  - The utility could not confirm the setting reliably; check it manually.

Game Mode note: If the tool shows VERIFY for Game Mode, open Windows Settings > Gaming > Game Mode and check whether it is On. VERIFY does not necessarily mean Game Mode is disabled.

IMPORTANT LIMITATIONS
---------------------
This is a system-readiness checklist, not a live CPU scheduler or CCD performance tester. A passing score means the expected software components were detected, not that every game will automatically run on the ideal CCD.

BIOS settings such as CPPC preference require manual verification. On custom Windows ISOs, removal of other Windows dependencies can also affect operation even when all checklist entries look correct. Validate actual game scheduling separately if needed.

The tool never installs drivers, edits the registry, changes power plans, or modifies Windows.

BUILD FROM SOURCE
-----------------
Source is written in Go using native Windows APIs. With Go installed on Windows, run:

  $env:GOOS='windows'
  $env:GOARCH='amd64'
  $env:CGO_ENABLED='0'
  go build -trimpath -ldflags='-H windowsgui -s -w' -o X3D_Checker.exe main.go

OFFICIAL REFERENCES
-------------------
AMD Ryzen chipset drivers and release notes:
https://www.amd.com/en/resources/support-articles/release-notes/RN-RYZEN-CHIPSET-8-09-28-1124.html

AMD chipset driver installation:
https://www.amd.com/en/resources/support-articles/faqs/CHIPSET-INSTALL.html

AMD Ryzen 9 9950X3D support:
https://www.amd.com/en/support/downloads/drivers.html/processors/ryzen/ryzen-9000-series/amd-ryzen-9-9950x3d.html

DISCLAIMER
----------
X3D Checker is an independent, unofficial diagnostic utility and is not affiliated with AMD or Microsoft. The executable is not digitally signed, so Windows may display an unknown-publisher or SmartScreen warning.
