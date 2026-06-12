---
title: "ATI graphical glitches"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by championboxes on 2010-08-16
Im having problems with the propitiatory ati driver... see pic attachment...

I have a integrated HD3000 (760G) 

This is my xorg.conf... this is from another install from about a month or so ago the glitches were still happening before I replaced it
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "75"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3200 3200
		Depth     24
	EndSubSection
EndSection

``` 


this is the output of lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```

can anybody tell me what I need to do to fix this?

---

### Post by sandyd on 2010-08-16
> **championboxes said:**
> Im having problems with the propitiatory ati driver... see pic attachment...

I have a integrated HD3000 (760G) 

This is my xorg.conf... this is from another install from about a month or so ago the glitches were still happening before I replaced it
```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "75"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3200 3200
        Depth     24
    EndSubSection
EndSection

```
this is the output of lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```can anybody tell me what I need to do to fix this?
what catalyst version are you using.
catalyst 10.6 had those problems, but the amount decreased in catalyst 10.7.
the propreity drivers are always somehwat buggy anyways...

---

### Post by championboxes on 2010-08-16
> **carlee said:**
> what catalyst version are you using.
catalyst 10.6 had those problems, but the amount decreased in catalyst 10.7.
the propreity drivers are always somehwat buggy anyways...

Im not really sure under information and software it says

```
Driver Packaging Version----- 8.723.1-100408a-098580C-ATI
2D Driver Version---------- 8.72.11
Catalyst Control Center Version------- 2.12
RandR Version 1.3
```

If you could link me to the correct drivers and instructions I would try that... I have gone to the ATI site and downloaded what I thought was the right driver then installed it with "sudo ./atidriver.sh" and after a restart, X will not start

---

### Post by sandyd on 2010-08-16
> **championboxes said:**
> Im not really sure under information and software it says

```
Driver Packaging Version----- 8.723.1-100408a-098580C-ATI
2D Driver Version---------- 8.72.11
Catalyst Control Center Version------- 2.12
RandR Version 1.3
```If you could link me to the correct drivers and instructions I would try that... I have gone to the ATI site and downloaded what I thought was the right driver then installed it with "sudo ./atidriver.sh" and after a restart, X will not start
I think your using an older version.
according to the manual, catalyst 10.7 is 8.753, not 8.72.11
tell me, have you tried disabling offscreen pixmaps?

---

### Post by championboxes on 2010-08-16
> **carlee said:**
> I think your using an older version.
according to the manual, catalyst 10.7 is 8.753, not 8.72.11
tell me, have you tried disabling offscreen pixmaps?

Um no could you describe how to do that I dont see any options for it in CCC

---

### Post by championboxes on 2010-08-16
> **carlee said:**
> I think your using an older version.
according to the manual, catalyst 10.7 is 8.753, not 8.72.11
tell me, have you tried disabling offscreen pixmaps?

Thanks for your help but I managed to fix my problem... for some reason if I installed the drivers from the website as root X would not start... so Installing it as a regular user worked

---

