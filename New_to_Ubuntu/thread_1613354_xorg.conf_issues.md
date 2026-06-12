---
title: "xorg.conf issues"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by DimmeysJeff on 2010-11-04
Hi, this is my first post on these forums, so please be gentle ;)

I have just installed MythBuntu on my old desktop (Intel P4 2Ghz, 1GB DDR, nVidia TNT2 card with TV out) with a view to using it as a cheap and cheerful media centre, so I am new to the whole Linux thing (this last week has been a learning curve to say the least).

Anyhoo, it seems that to make any changes to the way the system boots you need to modify the xorg.conf (I want to get the TV out on my graphics card working).

Trouble is, I don't have one, and furthermore, when I last auto-generated one using (I think) "sudo xorg -configure" and renamed it, it froze my system upon rebooting - I couldn't get back in to remove it and had to reinstall MythBuntu from scratch. Without xorg.conf however, it all boots up fine.

So I guess my questions are A. What could be causing my system to freeze up so badly with the xorg.conf, and B. is there a way to recover from a bad boot without having to re-install from scratch (apparently there's a 'recovery mode' but I don't know how to access it. I've also tried unsuccessfully to made a boot CD)

I will post up a copy of the file that the "sudo Xorg -configure" command generates once I figure out how.

Cheers, all input appreciated!

---

### Post by wojox on 2010-11-04
To create the xorg for nvidia try

```
sudo nvidia-xconfig
```

Then edit it with

```
gksudo nvidia-settings
```

---

### Post by DimmeysJeff on 2010-11-04
Here is the xorg/conf file that "Xorg -configure" generates...

```
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
     FontPath     "built-ins" EndSection  Section "Module"
     Load  "dbe"
     Load  "dri2"
     Load  "dri"
     Load  "extmod"
     Load  "record"
     Load  "glx"
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
         ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
         ### <percent>: "<f>%"
         ### [arg]: arg optional
         #Option     "SWcursor"
               # [<bool>]
         #Option     "HWcursor"
               # [<bool>]
         #Option     "NoAccel"
                # [<bool>]
         #Option     "ShadowFB"
               # [<bool>]
         #Option     "VideoKey"
               # <i>     Identifier  "Card0"
     Driver      "nouveau"
     BusID       "PCI:1:0:0"
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
```

---

### Post by dtfinch on 2010-11-04
You can hold down the shift key at boot to make the grub menu appear. It hides it by default if Ubuntu is the only OS installed.

---

