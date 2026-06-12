---
title: "Suspected problem with graphics"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Wiwa94 on 2010-09-22
I have a problem, in which at random times my computer will either  freeze and become unresponsive, or will revert to a black screen with  several vertical white lines on it, while the monitor turns itself off  and on repeatedly until I reboot.

 My computer is pretty old, 3.06 GHz processor, 1Gb RAM, Intel 82845G/GL/GE/PE/GV Graphics controller

I suspect that it is because I need to get a GPU, but it would be great  to have some input as to other reasons this could be happening.

In case you need it,
Xorg.conf:
 
 Section "ServerLayout"
     Identifier     "X.org Configured"
     Screen      0  "Screen0" 0 0
     InputDevice    "Mouse0" "CorePointer"
     InputDevice    "Keyboard0" "CoreKeyboard"
 EndSection
 
 Section "Files"
     ModulePath   "/usr/lib/xorg/modules"
     FontPath     "/usr/share/fonts/X11/misc"
     FontPath     "/usr/share/fonts/X11/cyrillic"
     FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
     FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
     FontPath     "/usr/share/fonts/X11/Type1"
     FontPath     "/usr/share/fonts/X11/100dpi"
     FontPath     "/usr/share/fonts/X11/75dpi"
     FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
     FontPath     "built-ins"
 EndSection
 
 Section "Module"
     Load  "glx"
     Load  "record"
     Load  "dri"
     Load  "dri2"
     Load  "dbe"
     Load  "extmod"
 EndSection
 
 Section "InputDevice"
     Identifier  "Keyboard0"
     Driver      "kbd"
 EndSection
 
 Section "InputDevice"
     Identifier  "Mouse0"
     Driver      "mouse"
     Option        "Protocol" "auto"
     Option        "Device" "/dev/input/mice"
     Option        "ZAxisMapping" "4 5 6 7"
 EndSection
 
 Section "Monitor"
     Identifier   "Monitor0"
     VendorName   "Monitor Vendor"
     ModelName    "Monitor Model"
 EndSection
 
 Section "Device"
         ### Available Driver options are:-
         ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
         ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
         ### [arg]: arg optional
         #Option     "NoAccel"                # [<bool>]
         #Option     "SWcursor"               # [<bool>]
         #Option     "ColorKey"               # <i>
         #Option     "CacheLines"             # <i>
         #Option     "Dac6Bit"                # [<bool>]
         #Option     "DRI"                    # [<bool>]
         #Option     "NoDDC"                  # [<bool>]
         #Option     "ShowCache"              # [<bool>]
         #Option     "XvMCSurfaces"           # <i>
         #Option     "PageFlip"               # [<bool>]
     Identifier  "Card0"
     Driver      "intel"
     VendorName  "Intel Corporation"
     BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
     BusID       "PCI:0:2:0"
 EndSection
 
 Section "Screen"
     Identifier "Screen0"
     Device     "Card0"
     Monitor    "Monitor0"
     SubSection "Display"
         Viewport   0 0
         Depth     1
     EndSubSection
     SubSection "Display"
         Viewport   0 0
         Depth     4
     EndSubSection
     SubSection "Display"
         Viewport   0 0
         Depth     8
     EndSubSection
     SubSection "Display"
         Viewport   0 0
         Depth     15
     EndSubSection
     SubSection "Display"
         Viewport   0 0
         Depth     16
     EndSubSection
     SubSection "Display"
         Viewport   0 0
         Depth     24
     EndSubSection
 EndSection

---

### Post by Paddy Landau on 2010-09-23
It sounds like hardware. I had a similar problem with bands, and it was a faulty graphics card or screen. I didn't get it fixed as its warranty had expired.

---

### Post by Rubi1200 on 2010-09-23
For Intel chipsets:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by grahammechanical on 2010-09-23
How old is your monitor? What make and model? The output that you have given does not give any information as to the monitor. There should be all kinds on info about the monitor. Perhaps the monitor is not recognised or does not have a driver. What information do you see under Preferences>Monitors? Could the Monitor cable be faulty? Perhaps one of the wires in the cable is breaking. This happened to me a few years ago. I had to cut back the cable and re-solder the D-Sub connector.

Regards

---

### Post by Wiwa94 on 2010-09-24
> **grahammechanical said:**
> How old is your monitor? What make and model? The output that you have given does not give any information as to the monitor. There should be all kinds on info about the monitor. Perhaps the monitor is not recognised or does not have a driver. What information do you see under Preferences>Monitors? Could the Monitor cable be faulty? Perhaps one of the wires in the cable is breaking. This happened to me a few years ago. I had to cut back the cable and re-solder the D-Sub connector.

Regards
The monitor is fine, recognised and has a driver. It is a Dell standard 17", same age as the computer, no problems that I can see with the cable.

---

### Post by Wiwa94 on 2010-09-24
> **Paddy Landau said:**
> It sounds like hardware. I had a similar problem with bands, and it was a faulty graphics card or screen. I didn't get it fixed as its warranty had expired.
Warranty has most certainly expired, as my computer is 7-ish years old. I'm going to buy a fairly cheap graphics card to see if things improve.

---

