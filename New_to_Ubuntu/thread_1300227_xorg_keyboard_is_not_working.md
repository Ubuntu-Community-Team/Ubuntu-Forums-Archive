---
title: "xorg keyboard is not working"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Vichfret on 2009-10-24
I configured my keyboard on xorg.conf but it doesn't seem to be working, it looks like it's ignoring my xorg.conf (just for the keyboard and the DontZap), but I can change my keyboard layout with the graphical tool but it's faster for me to change the layout using a key so I want to configure my xorg.conf. Here is my xorg.conf file

```
Section "ServerLayout"
    Identifier     "Main Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load "i2c"
    Load "ddc"
    Load "vbe"
    Load "dri"
    Load "glx"
    Load "synaptics"
EndSection

Section "ServerFlags"
    Option "AllowMouseOpenFail" "true"
    Option "Xinerama" "0"
    Option "DontZap" "false"
    #Option "AutoAddDevices" "false"
EndSection

Section "InputDevice"
    Identifier "Keyboard0"
    Driver "kbd" #man kbd
    Option "CoreKeyboard"
    Option "XkbModel" "pc105"
    Option "XkbRules" "xorg"
    Option "XkbLayout" "latam,us"
    Option "XkbVariant" ",intl" #/usr/share/X11/xkb/rules/xorg.lst
    #Option "XkbOptions" "grp:lwin_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
    Identifier "Mouse0"
    Driver "mouse"
    Option "Protocol"
    Option "Device" "/dev/input/mice"
    Option "Emulate3Buttons" "no"
    Option "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier "Monitor0"
    VendorName "Unknown"
    ModelName "CRT-1"
    HorizSync 30.0 - 83.0
    VertRefresh 56.0 - 75.0
EndSection

Section "Device"
    Identifier "Device0"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    BoardName "GeForce 8800 GS"
EndSection

Section "Screen"
    Identifier "Screen 0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    Option "AddARGBGLXVisuals" "true"
    Option "TwinView" "0"
    SubSection "Display"
        Depth 24
        Modes "1280x1024" "1152x870" "1024x768" "832x624" "800x600" "720x40" "640x400" "640x350"
    EndSubSection
EndSection


```

---

