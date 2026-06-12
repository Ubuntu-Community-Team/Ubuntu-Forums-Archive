---
title: "Dual Monitor Dilema"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by klemperal on 2009-01-30
I'm having some serious problems getting my TV working as a seperate x screen.  Although the TV stays black normally, when I hit the "detect display" button within nvidia-settings I can see my desktop flash on the TV for a second.  I'm using a nvidia 8400gs, 177 driver, and Ubuntu 8.10.  Some help getting things working would really be appreciated.  Below is my xorg.conf.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E151FPb"
    HorizSync       31.0 - 60.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       0.0 - 0.0
    VertRefresh     0.0
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
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:4:0:0"
    Screen          1
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
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "TV: 800x600 +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 800x600 +0+0; TV: 720x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection 
```

---

### Post by SteveDee on 2009-01-31
Under the Monitor section for monitor1 you have "0" for HorizSync & VertRefresh, hence the blank screen.

I suggest you look at the notes here:-
 [http://ubuntuforums.org/showthread.php?t=1023565](http://ubuntuforums.org/showthread.php?t=1023565)
which includes a copy of my xorg.conf file. I hope this helps.

---

