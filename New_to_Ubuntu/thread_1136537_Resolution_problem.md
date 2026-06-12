---
title: "Resolution problem"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by jestinjoy on 2009-04-25
I am using Ubuntu 9.04 now:). Its a great release. 

 I have Nvidia Geforce 6100. So I installed the nvidia driver. I adjusted the screen resolution to 1024x768. But when the next time I login it goes back to the default 640x480 configuration. My /etc/X11/xorg.conf file is given below..............

```
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
```


How to edit it so that 1024x768 is to be kept as my default resolution.

---

### Post by Peter09 on 2009-04-25
Try installing the nvidia-config manager its in the repositories.

---

### Post by jestinjoy on 2009-04-25
I cant find anything like nvidia-config. I installed nvidia-settings and changed the resolution to 1024x768. But it goes back to the old state in the next login.

---

### Post by Peter09 on 2009-04-25
These days Xorg.conf is really only used to force a configuration. It might be worth renaming your Xorg.conf -> Xorg.conf.saved or similar. Reboot,stand well back, and see what happens. 

Most 'standard' configs these days have virtually nothing in Xorg.

---

### Post by jestinjoy on 2009-04-25
where to change to set thedefault resolution to 1024x768

---

### Post by Peter09 on 2009-04-25
the x-server should identify your default resolutions, also in nvidia-settings and in System->Preferences->Display

---

### Post by Peter09 on 2009-04-25
This thread may help

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1127871](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1127871)

---

### Post by 4Orbs on 2009-04-25
Or you can change your "Screen" section to the below. You must edit the xorg.conf file as root by entering:

```
gksudo gedit /etc/X11/xorg.conf
```

Then replace your Screen section with this:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
  SubSection "Display"
    Depth 24
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
EndSection
```

Save the file then reboot.

---

### Post by jestinjoy on 2009-04-25
Thnaks...... It helped.... :guitar:


But one thing I noticed the ect/X11/xorg.conf shown in nvidia settings is bit different........It is given below...

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 55.0
    VertRefresh     50.0 - 120.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Why is it so..My orginal /etc/X11/xorg.conf was posted at the top post.:lolflag:

---

### Post by 4Orbs on 2009-04-25
Normally you should use the nVidia Settings Mgr as root user to change system default resolution:
```
gksudo nvidia-settings
```
Then save your changes to the xorg.conf by clicking on the button. But when I did that in Jaunty, I was no longer able to use compiz because the window borders disappeared. But everything works properly when I use the sparse, original xorg.conf with the added subsection and modes.

You might prefer using the nVidia Settings Mgr version of xorg.conf and maybe your Metacity window frames will survive.

---

