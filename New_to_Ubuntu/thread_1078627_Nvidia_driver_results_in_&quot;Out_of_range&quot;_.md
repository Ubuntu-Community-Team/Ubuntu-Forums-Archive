---
title: "Nvidia driver results in &quot;Out of range&quot; error"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Splappy on 2009-02-23
I installed the Nvidia graphics driver with the restricted driver manager, I think it was version 96.
I reboot, and I get a "Out of range" error from the monitor.
I can get to the CLI with Ctrl+Alt+F1, I'd try and edit the xorg.conf but I can't remember where it's located. :p

Ubuntu 8.10 on a Emachines EL1200-07w, and I don't know exactly what Nvidia graphics card is in it. (Reeeeal helpful when you have a problem, right? :p) The monitor is a Synaps 19" LCD monitor connected via VGA with a native resolution of 1280x1024.

---

### Post by taurus on 2009-02-23
Your xorg.conf is in /etc/X11/xorg.conf.

And to find out the model of your nvidia card, run

```
lspci | grep VGA
```

---

### Post by Splappy on 2009-02-23
"lspci | grep VGA" says this:
```
00:0d,0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
```

And my xorg.conf contains this, minus the comments at the top:
```
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Monitor        "Configured Monitor"
    Device         "Configured Video Device"
    DefaultDepth   24
    Option  "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver "nvidia"
    Option  "NoLogo"      "True"
EndSection
```
(i typed that manually, there might be some mistakes)
Could I just change the Driver line in the Device section to "nv" and atleast have a gui?
This is the first time I've ever had to deal with Nvidia graphics cards, so...yeah. :p

---

