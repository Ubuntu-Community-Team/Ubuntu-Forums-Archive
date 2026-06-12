---
title: "4:3 resolution on 16:10 monitor with black bars"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Anuovis on 2009-11-22
Hello,
I have a 1280x800 laptop monitor and I would sometimes like to switch to 1024x768. Problem is that the aspect ratios do not match and it ends up stretched across the screen. I looked in the forums and found [COLOR=Blue]**_[this thread]("http://ubuntuforums.org/showthread.php?t=660609")_**[/COLOR] 

My etc/X11/xorg.conf now looks like this:

> 
Section "Device"
    Identifier    "Configured Video Device"
        Option          "AccelMethod"  "XAA"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"

  [B]      SubSection "Display"
                Modes   "1280x800" "1024x768"
Option  "Centermode"    "on"
                Option  "NoStretch"     "on"
        EndSubSection[/B]

EndSection

Lines **in bold** are the ones that I added myself. I do not know how or why but I had a xorg.conf.txt file in my trash which I created or deleted at some time... I used it as a base for creating this one.

However, switching to 1024 resolution after restart still stretches it to fill the whole screen. I am not sure if my conf file is improper or the system just does not detect it. Maybe I should try something completely different for this to work.

My card is ATI Mobility Radeon x1400 running on open Ubuntu drivers (at least I think so...)

Any ideas on how to run a 1024 letter-boxed resolution would be very useful.

---

### Post by Anuovis on 2009-11-23
Bump-update.

I generated an xorg.conf file on my system. Can I add something to it that would work in 9.10 and solve my question? Or should I take an entirely different path?

I would like to know if I am headed to the correct direction, not necessary a straightforward answer. 

Can modification of xorg.conf solve this issue?
Is it a video car/driver specific one?
How do you deal with video issues in 9.10 if xorg.conf is not present by default? Any other places to do that?

Any hints would be very appreciated.
Thank you


[html]Section "ServerLayout"
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
    Load  "dri"
    Load  "dri2"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
    Load  "record"
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
    #DisplaySize      330   210    # mm
    Identifier   "Monitor0"
    VendorName   "AUO"
    ModelName    "1c74"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon Mobility X1400"
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
EndSection[/html]

---

### Post by Jabran Asghar on 2009-12-04
Hi,

Did you find a solution to this? I am looking for an answer for the same question.

Jabran

---

### Post by Ocxic on 2009-12-04
Try changing 

```

Section "Device"
Identifier    "Configured Video Device"
Option          "AccelMethod"  "XAA"
EndSection

Section "Monitor"
Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"

[B]SubSection "Display"
Modes   "1280x800" "1024x768"
Option  "Centermode"    "on"
Option  "NoStretch"     "on"
EndSubSection[/B]

EndSection


```to:

```

Section "Device"
Identifier    "Configured Video Device"
Option          "AccelMethod"  "XAA"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"[B]
Modes   "1280x800" "1024x768"
Option  "Centermode"    "on"
Option  "NoStretch"     "on"
[/B]EndSection


```

---

### Post by Anuovis on 2009-12-05
Ocxic, thank you for the reply, but I just gave up and went back to Windows for a while. 

It was just too complicated for me to figure out. Now I do not need this feature any more. Sorry, forgot to close this thread.

There is another thread with an almost exact question. I contacted the poster and we shared some frustration about this topic :) So far, there seems to be no answer. Jabran, you might want to **_[take a look at it]("http://ubuntuforums.org/showthread.php?t=1334211")_** . 

I am not sure if I should leave my thread as it is or mark it as solved, but I think it is better to continue the discussion on the linked one.

---

