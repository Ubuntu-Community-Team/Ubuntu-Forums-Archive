---
title: "Refresh rate"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by James5 on 2009-08-03
Hi, new to Ubuntu here, and I can't get a refresh rate higher than 60hz.
My monitor is a HP Ultra VGA 1280 CRT, specs here:

[http://www.monitorworld.com/Monitors/hp/hpultravga1280.html](http://www.monitorworld.com/Monitors/hp/hpultravga1280.html)

Here is a copy of my Xorg file:
```
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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
    ModelName      "CRT-1"
    # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHzModeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsyn
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```I've tried everything, but can't understand what I have done wrong!
If someone could fix this for me, I'd be really grateful!

---

### Post by realzippy on 2009-08-03
Open your xorg.conf  with gedit:

sudo gedit /etc/X11/xorg.conf

Delete the "#" in the modline:

# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHzModeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsyn

Then restart (xserver)

---

### Post by realzippy on 2009-08-03
..by the way,did you try setting refresh rate with nvidia-settings?
If not:

gksudo nvidia-settings

choose desired refresh rate and hit (important!!):

"save to xorg"

then restart xserver

---

### Post by James5 on 2009-08-03
With a bit of fiddling and trial and error, I've managed to fix it, and now have it at 1024x768 @ 75hz!

Here is the current Xorg file:

```
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       30.0 - 69.0
    VertRefresh     50.0 - 132.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```Thanks a lot, made my day!

---

