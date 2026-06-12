---
title: "problem installing nvidia-xconfig"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by mysticaltopher on 2009-03-24
I'm trying to get my friends screen resolution bumped up to 1024x768 and so i installed nvidia-xconfig through the terminal.  It removed the nvidia-gxt-73 (or whatever it was) and installed nvidia-xconfig.  But now when I type nvidia-xconfig into the terminal it tells me that the info in xorg.conf is incomplete because their is no driver line in the code and wont start because of it.  So what do I need to do to allow the xconfig to run?

Here's the actual terminal line:

chris@chris-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.

chris@chris-desktop:~$





If anyone knows whats up please help, I've been trying to fix this problem for weeks now but keep running into little gliches....he is using a nvidia TNT2 card which is not compatible with Ubuntu 8.10 so I'm trying to figure out how to crack the system to allow the new resolution (instead of the default 800x600)

Thanks!!

---

### Post by rockstone on 2009-03-24
Presumably it wants to you to edit the xorg.conf file because of some error in the configuration (no device driver specified). 

```
gksudo gedit /etc/X11/xorg.conf
```

If you delete the xorg.conf file it should remake it with default settings.

```
sudo rm /etc/X11/xorg.conf
```

Or if you have settings that you want to keep you could post the contents here to see what is missing.

The line that is missing is probably:

```

Section "Device"
**	Driver         "***"**
EndSection
```

In my case *** = nvidia.

---

### Post by mysticaltopher on 2009-03-24
his xorg.conf file reads as such:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


will:    Driver  "nvidia"   :work?

---

