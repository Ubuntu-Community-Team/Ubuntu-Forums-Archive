---
title: "Three Monitors"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by moab on 2010-04-20
I am having trouble setting up my third monitor... every time I move the mouse over to the third monitor, the cursor shakes violently and freezes the machine. Does anyone know what could be causing this?

[LIST]
[*]I have two 8600GT (nvidia) graphics cards and I am using NVIDIA X server settings to set this up. 
[*]The first monitor is one card, and the other two are on the second. 
[*]I have Xinerama enabled and separate X screens.
[*]The third monitor is an LCD TV with 1920x1080.
[*]Everything is on VGA cables.
[*]Programs can open in the third monitor just fine, but moving the mouse over freezes the system.
[*]I am using the current drivers (not 173, those won't even allow startup).
[*]I am running 10.04.
[/LIST]

Apologies if I'm posting in the wrong spot, this is my first real problem with Ubuntu.

---

### Post by LowSky on 2010-04-20
10.04 is still in BETA. We really can't help you with your issue.

I know its not the answer your looking for but Beta software is harder to diagnose as it could any giving application that still requires tweeking. Also because updates are still occuring daily the problem could be fix by the next update or even broken. That is why no one reccomends Beta software on important machines.

---

### Post by Aesso on 2010-04-30
Hey guys, now that Lucid has been released, I was wondering if any headway has been made with this issue.

I'm having the same problem the original poster is having; my three-monitor setup was working flawlessly under Karmic and is now broken in Lucid.

After *hour upon hour* of frustrated searching (and consciously trying to remember not to stray the mouse too far to the left :) ), I finally discovered I was experiencing a _[known bug with XOrg 1.7](https://bugs.freedesktop.org/show_bug.cgi?id=24986)_ and monitors that are positioned "LeftOf" another display. 

I have three monitors on two NVIDIA GeForce 9400 GT cards. I'm using the NVIDIA driver 195.36.15. 

```

+-----------+ +-----------+ +-----------+
|     1     | |     2     | |   3       | 
|  Screen1  | |  Screen0  | |  Screen2  | 
+-----------+ +-----------+ +-----------+

| PCI 2     | | PCI 1                   |
| 2nd video | | 1st video card          |

```

Here's my original xorg.conf:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1680 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
    Option         "AIGLX" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "XGL" "true"

Section "Files"

	#RgbPath         "/usr/X11R6/lib/X11/rgb"
	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2002W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL2002W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Acer AL2002W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"

    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"

    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"

    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Waiting for this to be fixed, I temporarily changed my xorg.conf so that my Screen0 is the one farthest to the left. While I find this extremely annoying (I want my Screen0 to be the middle display), this is manageable until a solution has been found. It's much better than the X server crashing.

Now my screens are ordered like this:
```

+-----------+ +-----------+ +-----------+
|     1     | |     2     | |   3       | 
|  Screen0  | |  Screen1  | |  Screen2  | 
+-----------+ +-----------+ +-----------+

| PCI 2     | | PCI 1                   |
| 2nd video | | 1st video card          |

```

Here is how my xorg.conf looks now:
```
 
Section "ServerLayout"

    Identifier     "Layout0"
    #Screen      1  "Screen1" LeftOf "Screen0"
    #Screen      0  "Screen0" 1680 0
    #Screen      2  "Screen2" RightOf "Screen1"
    Screen 0 "Screen0" 0 0 
    Screen 1 "Screen1" RightOf "Screen0"
    Screen 2 "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
    Option         "AIGLX" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "XGL" "true"
EndSection

Section "Files"

	#RgbPath         "/usr/X11R6/lib/X11/rgb"
	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2002W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL2002W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Acer AL2002W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
	# HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Device"

    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"

    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:1:0:0"
    Screen         0
EndSection

Section "Device"

    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Any ideas how to get around this problem besides what I've already done? Is there a way to downgrade XOrg to version 1.6 until a new version comes out?

---

### Post by johansson.seb on 2010-05-08
Registered as [Bug #563100]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100").

---

### Post by nickmp on 2011-03-04
has this been fixed?
Im having a problem with the twinview. I have a N94GT-MD512 GeForce 9400 GT with 3 outputs. so twinview should work because all 3 monitors are on the same device correct? but i can only get two monitors to work on xserver. how do i get the 3rd to come on

---

