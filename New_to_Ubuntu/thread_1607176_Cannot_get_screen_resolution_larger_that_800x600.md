---
title: "Cannot get screen resolution larger that 800x600"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by topshotter on 2010-10-27
Hi

I am new to ubuntu. I have a dell precision 340 with a 32mb ATI Rage 128 Ultra Graphics Card connected to a dell 18inch monitor that supports 1280x1024 at 60Hz screen res. After installing ubuntu 10.10 my screen resolution has a max configuration of 800x600. I have read various articles regarding xorg.conf (which doesn't exist on my pc) cvt and xrandr commands but so far none have resulted in a fix. Can someone point me in the direction of a real solution even if its to simply buy a newer video card.

Thanks

---

### Post by bioterror on 2010-10-27
You have logged into a TTY with ctrl+alt+f1 (X is F7!) and run "sudo service stop gdm", run (sudo) "Xorg -configure", then moved that just created xorg.conf.nwq to the /etc/X11/ with "sudo mv xorg.conf.new /etc/X11/xorg.conf" command?
And then restored gdm back with "sudo service gdm start" and pressed ctrl+alt+f7.

If so, is it possible to paste that xorg.conf to us?

---

### Post by Mark Phelps on 2010-10-27
Unfortunately, if the hand-crafted xorg.conf doesn't fix this, your only recourse will be to purchase a new card.  AMD dropped proprietary driver support for your card in Linux long ago, so now, the drivers you already have installed are the only ones available.

To use the newer drivers, you will need a new card.

---

### Post by topshotter on 2010-10-27
Bioterror, thanks for your prompt response. I did what you suggested and have pasted the content of the xorg.conf file below.

I decided to install ubuntu because my mothers old pc with windows was only going to get infected with a multitude of spyware programs etc so i thought i'd try something different. Ah well. Hopefully you have an answer even if that is for me to buy a new video card.

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
    Load  "dri"
    Load  "glx"
    Load  "dbe"
    Load  "extmod"
    Load  "record"
    Load  "dri2"
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
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "ForcePCIMode"           # [<bool>]
        #Option     "CCEPIOMode"             # [<bool>]
        #Option     "CCENoSecurity"          # [<bool>]
        #Option     "CCEusecTimeout"         # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "Display"                # <str>
        #Option     "PanelWidth"             # <i>
        #Option     "PanelHeight"            # <i>
        #Option     "ProgramFPRegs"          # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "ShowCache"              # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
    Identifier  "Card0"
    Driver      "r128"
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

---

### Post by bioterror on 2010-10-30
Okay, let's have a try.

I made some minor changes, hope these works for you.
```

Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "Module"
Load "dri"
Load "glx"
Load "dbe"
Load "extmod"
Load "record"
Load "dri2"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Device"
Identifier "Card0"
Driver "r128"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Depth 24
Modes "1280x1024"
Viewport 0 0
EndSubSection
EndSection

```

---

### Post by swvan on 2010-10-30
Similar situation here. I have an old Dell Latitude C600 that has ATI 128 Rage Mobility. Also stuck in 800x600. WinXP will do 1024x768. I was able to get the wifi fixed with a new card and diver update. I really like 10.10, but the screen is driving me nuts as well as trying to figure out all of the Command stuff. It is a shame that there isn't a good GUI for this. I've read that it was dropped several versions back. Any way to get it? Any help would be appreciated.

---

### Post by bioterror on 2010-10-30
> **swvan said:**
> Similar situation here. I have an old Dell Latitude C600 that has ATI 128 Rage Mobility. Also stuck in 800x600. WinXP will do 1024x768. I was able to get the wifi fixed with a new card and diver update. I really like 10.10, but the screen is driving me nuts as well as trying to figure out all of the Command stuff. It is a shame that there isn't a good GUI for this. I've read that it was dropped several versions back. Any way to get it? Any help would be appreciated.

[http://ubuntuforums.org/showthread.php?t=828588]("http://ubuntuforums.org/showthread.php?t=828588")

Not so sure about the "ati" driver any more.
But worth to try.

---

### Post by swvan on 2010-10-30
Thanks Bioterror! This works perfectly! I have been fighting with this since 10.10 was released. Lost track of the number of reinstalls with botched tries.

---

### Post by Peterfc on 2010-11-24
> **bioterror said:**
> You have logged into a TTY with ctrl+alt+f1 (X is F7!) and run "sudo service stop gdm", run (sudo) "Xorg -configure", then moved that just created xorg.conf.nwq to the /etc/X11/ with "sudo mv xorg.conf.new /etc/X11/xorg.conf" command?
And then restored gdm back with "sudo service gdm start" and pressed ctrl+alt+f7.

If so, is it possible to paste that xorg.conf to us?

Like many i can't change the resolution either. I am sorry but i do not understand what you have posted.

On another reply i found /etc/X11/xorg.conf but i can't find this on my machine.

I am using a Toshiba 32in TV as my monitor. my resolution is set at 

1280 X 1024 (5:4)
Refresh 0hz
Rotation Normal

Peter

---

