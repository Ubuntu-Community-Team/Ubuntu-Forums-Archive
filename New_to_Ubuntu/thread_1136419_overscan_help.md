---
title: "overscan help?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by CloneRanger on 2009-04-25
I've searched the forum but i cannot find an answer simple enough for my little noob brain to understand.:lolflag:
I'm running ubuntu 9.04.

i'm using a single monitor (generic made in china 37" tv) with the nvidia accelerated graphics driver (version 180) over hdmi on my 8500GT graphics card at 1280x720 but i'm getting bad overcan and i havent got a clue how to resolve it, there are no options on the tv to sort out the problem. any help would be much appreciated

thanks in advance:)

---

### Post by nandemonai on 2009-04-25
You could try playing with the nvidia settings app. System -> Adminstration -> Nvidia X Server Settings.

If it's not installed then in terminal:

```
sudo apt-get install nvidia-settings
```

Best I can do I'm afraid.

---

### Post by CloneRanger on 2009-04-25
hey thanks for the help but i've tried altering the setting in there but no joy, its killing me this little problem is the only thing stopping me from loving the OS.

thank anway

someone's got to have a simple fix it seems like a common problem [-o<

---

### Post by CloneRanger on 2009-04-25
hi i've been looking around and i think i know what i have to do i just dont know how to do it i think i've got to edit the values in xorg.conf but i'm not sure which ones

again any help would be much appreciated

content of xorg.conf:


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

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
    ModelName      "YHI 37V1H-A6A"
    HorizSync       24.0 - 60.0
    VertRefresh     50.0 - 85.0
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
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1453 1536
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: 1260x720_60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0; DFP: 1280x720_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by nandemonai on 2009-04-25
Are you positive there are no 'auto adjust' settings on the TV itself? Mine is fairly generic itself and does have the option to auto adjust. That said, I'm using a VGA connection and not HDMI.

The only other thing I would suggest is to ensure you have the right refresh rates in the xorg.conf though I doubt that would have any impact on overscan.

---

### Post by David Valentine on 2009-04-27
These [instructions]("http://ubuntuforums.org/showthread.php?t=1003099") should help you.  It takes a bit of fiddling to deal with overscan issues, but it's doable.  I posted a shortcut on page 4 of that thread to help save a bit of time.

---

### Post by mcduck on 2009-04-27
> **CloneRanger said:**
> I've searched the forum but i cannot find an answer simple enough for my little noob brain to understand.:lolflag:
I'm running ubuntu 9.04.

i'm using a single monitor (generic made in china 37" tv) with the nvidia accelerated graphics driver (version 180) over hdmi on my 8500GT graphics card at 1280x720 but i'm getting bad overcan and i havent got a clue how to resolve it, there are no options on the tv to sort out the problem. any help would be much appreciated

thanks in advance:)

Are you sure 1280x720 is the right resolution for your display? You said it's a TV, and 1280x720 sounds like it's a "HD-Ready", so are you trying to run it at 720p mode?

Most "HD-Ready" TV's actually have a native resolution of 1366x768, which is what you should use if you want a pixel-perfect picture that fills the whole screen without any scaling.

---

