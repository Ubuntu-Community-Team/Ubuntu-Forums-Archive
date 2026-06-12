---
title: "Please help, Resolution"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by CullinHoneycutt on 2010-03-11
I am having a problem with the resolution or something on my ubuntu 9.10 ppc.
Everything is pixilated and the colour is off. I am a biggener in this and i have no idea how to fix the problem, when I go to System>Preferences>Display it only shows 1024x768 4:3 and wont let me change it, the refresh rate is stuck at 75 and I don't even know if this means anything regarding the problem. I am on an iMac G3 and when i go to nano or gedit this is what I get.
Section "Device"
    Identifier    "Configured Monitor"
    BusID        "PCI:6:3:0"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

If any one knows how to help it would be much appreciated.


-Cullin

---

### Post by Daveth on 2010-03-13
that sounds more like graphic drivers than resolution, especially the pixelation *and* the colour shift. Have you enabled any graphics drivers? Never played with an iMac so rather at a loss....

---

