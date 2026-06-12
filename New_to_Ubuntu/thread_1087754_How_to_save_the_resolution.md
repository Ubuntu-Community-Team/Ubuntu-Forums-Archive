---
title: "How to save the resolution?"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by makkirot on 2009-03-05
Hello Linux geeks,
I am new to Ubuntu 8.10 but i enjoy a lot.
My question is that everytime i restart the computer i get the default screen resolution and every time i have to change it manually.
i.e, I have to go to Nvidia X Server settings, and there i have to change to 1152 * 864 .
When i try to save i get the message .Unable to create new X config backup file '/etc/X11/xorg.conf.backup'...

And also it is unable to overright the file /etc/X11/xorg.conf.
The default display is. 
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

But the save content's preview is.. 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1152x864 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

..
So what should i Do , so that the default resou;tion coud be 1152*864.
I have Geforce 7300GT graphics card , and  21' CRT viewsonic Monitor.. 
Need help please.. 
Thanks in Advance.. :D

---

### Post by bsharp on 2009-03-05
Push Alt+F2 and type:
```
gksudo nvidia-settings
```

Make your changes and save them like you tried before.

---

### Post by makkirot on 2009-03-06
> **bsharp said:**
> Push Alt+F2 and type:
```
gksudo nvidia-settings
```

Make your changes and save them like you tried before.
No dude.. Its not working.. :(:(

---

