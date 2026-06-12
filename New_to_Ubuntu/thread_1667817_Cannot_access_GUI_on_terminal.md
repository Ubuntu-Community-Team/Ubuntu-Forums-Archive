---
title: "Cannot access GUI on terminal"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by pilotguy415 on 2011-01-15
**I apologize in advance for the long post**
 
I received a CR-48 from google which works awesome but has its limitations due to being strictly web based. So I installed ubuntu on it without problems (ok it was a huge headache but I got it working).
 
Anyway, the trackpad works but not well. It is not sensitive and the scrolling does not work. So I found some tips on how to fix it. Turns out I need to downgrade xorg. 
 
So, I did that, and part of the process is editing the xorg.conf. I edit exactly as stated using VI in virtual terminal. Once the edits are complete I saved the file and start gdm again. The terminal shows it has started so I hit ctrl+alt+F7. I get a black screen with a flashing curser in the top left. Reboot computer...gives me a terminal login screen. 
 
Everything I have tried gives me either errors or does nothing.
 
Here is the contents of the xorg.conf file maybe someone with more knowledge then me can figure out if something is wrong on it.
 
```

[FONT=Courier New][SIZE=2]Section "ServerLayout"[/SIZE][/FONT]
[SIZE=2][FONT=Courier New]     Identifier     "X.org Configured"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Screen      0  "Screen0" 0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     InputDevice    "Mouse0" "CorePointer"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     InputDevice    "Keyboard0" "CoreKeyboard"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Section "Files"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     ModulePath   "/usr/lib/xorg/modules"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/misc"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/cyrillic"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/Type1"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/100dpi"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/75dpi"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "built-ins"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Section "Module"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "dbe"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "dri"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "dri2"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "extmod"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "glx"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "record"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Section "InputDevice"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Identifier  "Keyboard0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Driver      "kbd"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[FONT=Courier New][SIZE=2][COLOR=black]**Section "InputDevice"**[/COLOR][/SIZE][/FONT]
**[SIZE=2][FONT=Courier New][COLOR=black]     Identifier  "Mouse0"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]     Driver      "syntp"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]     Option          "Device" "/dev/input/mice"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]     ption     "SendCoreEvents" "true"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]EndSection[/COLOR][/FONT][/SIZE]**
 
**[SIZE=2][FONT=Courier New][COLOR=black]#Section "InputDevice"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#        Identifier "Mouse0"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#        Driver     "mouse"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#        Option     "Protocol" "auto"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#        Option     "Device" "/dev/input/mice"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#        Option     "ZAxisMapping" "4 5 6 7"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#EndSection[/COLOR][/FONT][/SIZE]**
 
[SIZE=2][FONT=Courier New]Section "Monitor"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Identifier   "Monitor0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     VendorName   "Monitor Vendor"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     ModelName    "Monitor Model"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Section "Device"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       ### Available Driver options are:-[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       ### [arg]: arg optional[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "NoAccel"            # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "SWcursor"           # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "ColorKey"           # <i>[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "CacheLines"         # <i>[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "Dac6Bit"            # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "DRI"                # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "NoDDC"              # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "ShowCache"          # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "XvMCSurfaces"       # <i>[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "PageFlip"           # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Identifier  "Card0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Driver      "intel"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     VendorName  "Intel Corporation"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     BoardName   "N10 Family Integrated Graphics Controller"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     BusID       "PCI:0:2:0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Section "Screen"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Identifier "Screen0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Device     "Card0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Monitor    "Monitor0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     1[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     4[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     8[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     15[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     16[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     24[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]

```

[FONT=Courier New]I bolded the only area that was meant to be changed.[/FONT]

[FONT=Courier New]Thanks for any help![/FONT]

---

### Post by sandyd on 2011-01-15
> **pilotguy415 said:**
> **I apologize in advance for the long post**
 
I received a CR-48 from google which works awesome but has its limitations due to being strictly web based. So I installed ubuntu on it without problems (ok it was a huge headache but I got it working).
 
Anyway, the trackpad works but not well. It is not sensitive and the scrolling does not work. So I found some tips on how to fix it. Turns out I need to downgrade xorg. 
 
So, I did that, and part of the process is editing the xorg.conf. I edit exactly as stated using VI in virtual terminal. Once the edits are complete I saved the file and start gdm again. The terminal shows it has started so I hit ctrl+alt+F7. I get a black screen with a flashing curser in the top left. Reboot computer...gives me a terminal login screen. 
 
Everything I have tried gives me either errors or does nothing.
 
Here is the contents of the xorg.conf file maybe someone with more knowledge then me can figure out if something is wrong on it.
 
```

[FONT=Courier New][SIZE=2]Section "ServerLayout"[/SIZE][/FONT]
[SIZE=2][FONT=Courier New]     Identifier     "X.org Configured"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Screen      0  "Screen0" 0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     InputDevice    "Mouse0" "CorePointer"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     InputDevice    "Keyboard0" "CoreKeyboard"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Section "Files"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     ModulePath   "/usr/lib/xorg/modules"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/misc"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/cyrillic"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/Type1"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/100dpi"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/usr/share/fonts/X11/75dpi"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     FontPath     "built-ins"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Section "Module"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "dbe"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "dri"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "dri2"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "extmod"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "glx"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Load  "record"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Section "InputDevice"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Identifier  "Keyboard0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Driver      "kbd"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[FONT=Courier New][SIZE=2][COLOR=black]**Section "InputDevice"**[/COLOR][/SIZE][/FONT]
**[SIZE=2][FONT=Courier New][COLOR=black]     Identifier  "Mouse0"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]     Driver      "syntp"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]     Option          "Device" "/dev/input/mice"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]     ption     "SendCoreEvents" "true"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]EndSection[/COLOR][/FONT][/SIZE]**
 
**[SIZE=2][FONT=Courier New][COLOR=black]#Section "InputDevice"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#        Identifier "Mouse0"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#        Driver     "mouse"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#        Option     "Protocol" "auto"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#        Option     "Device" "/dev/input/mice"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#        Option     "ZAxisMapping" "4 5 6 7"[/COLOR][/FONT][/SIZE]**
**[SIZE=2][FONT=Courier New][COLOR=black]#EndSection[/COLOR][/FONT][/SIZE]**
 
[SIZE=2][FONT=Courier New]Section "Monitor"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Identifier   "Monitor0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     VendorName   "Monitor Vendor"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     ModelName    "Monitor Model"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Section "Device"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       ### Available Driver options are:-[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       ### [arg]: arg optional[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "NoAccel"            # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "SWcursor"           # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "ColorKey"           # <i>[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "CacheLines"         # <i>[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "Dac6Bit"            # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "DRI"                # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "NoDDC"              # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "ShowCache"          # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "XvMCSurfaces"       # <i>[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       #Option     "PageFlip"           # [<bool>][/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Identifier  "Card0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Driver      "intel"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     VendorName  "Intel Corporation"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     BoardName   "N10 Family Integrated Graphics Controller"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     BusID       "PCI:0:2:0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New]Section "Screen"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Identifier "Screen0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Device     "Card0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     Monitor    "Monitor0"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     1[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     4[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     8[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     15[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     16[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     SubSection "Display"[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Viewport   0 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]           Depth     24[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]     EndSubSection[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]EndSection[/FONT][/SIZE]

```[FONT=Courier New]I bolded the only area that was meant to be changed.[/FONT]

[FONT=Courier New]Thanks for any help![/FONT]
you know....
running
```

sudo X -configure
```
will solve all your problems right?

---

