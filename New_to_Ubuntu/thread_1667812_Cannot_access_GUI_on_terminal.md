---
title: "Cannot access GUI on terminal"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by pilotguy415 on 2011-01-15
**I apologize in advance for the long post**
**sorry about the triple post as well, my internet messed up**
 
I received a CR-48 from google which works awesome but has its limitations due to being strictly web based. So I installed ubuntu on it without problems (ok it was a huge headache but I got it working).
 
Anyway, the trackpad works but not well. It is not sensitive and the scrolling does not work. So I found some tips on how to fix it. Turns out I need to downgrade xorg. 
 
So, I did that, and part of the process is editing the xorg.conf. I edit exactly as stated using VI in virtual terminal. Once the edits are complete I saved the file and start gdm again. The terminal shows it has started so I hit ctrl+alt+F7. I get a black screen with a flashing curser in the top left. Reboot computer...gives me a terminal login screen. 
 
Everything I have tried gives me either errors or does nothing.
 
Here is the contents of the xorg.conf file maybe someone with more knowledge then me can figure out if something is wrong on it.
 
```

[FONT=Courier New][SIZE=2]Section "ServerLayout"
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
      Load  "dbe"
      Load  "dri"
      Load  "dri2"
      Load  "extmod"
      Load  "glx"
      Load  "record"
EndSection

Section "InputDevice"
      Identifier  "Keyboard0"
      Driver      "kbd"
EndSection
 
[/SIZE][SIZE=2][COLOR=black][B]Section "InputDevice"
      Identifier  "Mouse0"
      Driver      "syntp"
      Option          "Device" "/dev/input/mice"
      ption     "SendCoreEvents" "true"
EndSection
 
#Section "InputDevice"
#        Identifier "Mouse0"
#        Driver     "mouse"
#        Option     "Protocol" "auto"
#        Option     "Device" "/dev/input/mice"
#        Option     "ZAxisMapping" "4 5 6 7"
#EndSection
[/B]
[/COLOR]Section "Monitor"
      Identifier   "Monitor0"
      VendorName   "Monitor Vendor"
      ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            # [<bool>]
        #Option     "SWcursor"           # [<bool>]
        #Option     "ColorKey"           # <i>
        #Option     "CacheLines"         # <i>
        #Option     "Dac6Bit"            # [<bool>]
        #Option     "DRI"                # [<bool>]
        #Option     "NoDDC"              # [<bool>]
        #Option     "ShowCache"          # [<bool>]
        #Option     "XvMCSurfaces"       # <i>
        #Option     "PageFlip"           # [<bool>]
      Identifier  "Card0"
      Driver      "intel"
      VendorName  "Intel Corporation"
      BoardName   "N10 Family Integrated Graphics Controller"
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
[/SIZE]
```[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]I bolded the only area that was meant to be changed.[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]Thanks for any help![/FONT]

---

