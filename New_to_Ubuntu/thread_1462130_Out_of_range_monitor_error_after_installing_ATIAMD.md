---
title: "Out of range monitor error after installing ATI/AMD proprietary driver"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by completely new on 2010-04-25
I have asus radeon ah2600 and I tried installing the proprietary drivers and now my monitor displays out of range error. I tried pressing alt+ctrl+f1, but then my monitor just turns off. I tried typing the commands blindly, but that didn't work, especially since I'm not sure which keyboard layout is being used. Please help me, I don't want to reinstall ubuntu yet again, how can I remove the drivers or make them work? I have 9.10 btw.

EDIT: I'm writing this from the live cd.

---

### Post by cryptotheslow on 2010-04-25
From the LiveCD you will need to make sure the partition where your installed version lives is mounted.

Then you can try fixing the refresh rates and resolution in the xorg.conf file (found in /etc/X11).

Make a copy of it before you start messing with it!


```
cd /etc/X11
sudo cp xorg.conf xorg.backup
sudo nano /etc/X11/xorg.conf
```Once you have it open in nano with the above check for the values in these 2 sections below - specifically the boldened lines to make sure they are in range for your monitor.

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    [B]HorizSync       31.0 - 70.0
    VertRefresh     50.0 - 75.0[/B]
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    **Option         "metamodes" "1024x768_75 +0+0"**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by completely new on 2010-04-25
My xorg.conf file doesn't have anything of that. It looks like this>
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

```:confused:

---

### Post by cryptotheslow on 2010-04-25
Try amending your "Screen" section to include the Option "metamodes" line and just add the Section "Monitor" in.

As long as you have taken a backup copy of xorg.conf before you start you can always put it back if it doesn't help :)

---

### Post by completely new on 2010-04-25
It didn't work, still the same problem. Any tips on removing the driver? I think that would be the easiest solution.

---

### Post by cryptotheslow on 2010-04-25
Backup the xorg.conf file then delete it (sudo rm /etc/X11/xorg.conf) - then reboot.

This should revert X to using the non-proprietary driver.

---

### Post by completely new on 2010-04-25
It worked, everything's fine now. Thanks. :)

---

### Post by allenlorenz on 2011-10-29
When install xbuntu on my 11.10 on  my llano system I got the blank monitor (with orange light indicator), implying no vga signal probably due to cause you noted above.   To solve this I restarted the install and pressed F6 selecting the nomodeset option to be passed to the install.  This allowed me to perform the install and selecting recovery mode from the grub menu to log into the system in text mode.

---

### Post by kurochan89 on 2012-12-23
I know this is a solved topic, but the solution isn't a real solution.
The proper way to solve the problem is:

[LIST=1]
[*]install ati proprietary driver (google it for ubuntu 12.10 procedure)
[*]after doing amdconfig --initial, BEFORE REBOOTING, use amdconfig and set hsync and refresh rate doing as super-user (e.g.):
[/LIST]
[INDENT][INDENT]amdconfig --hsync=0,59-59
amdconfig --vrefresh=0,59-59
amdconfig --resolution=0,1366x768
[/INDENT][/INDENT]Of course, this tells amdconfig to set the various frequency and resolution to desired value, instead of default ones (which use 75hz).
This worked for my 18.5" wide led monitor which only accepted 60hz, instead ati proprietary driver starts with 75hz.
I know it is late, but in case point me to the newest topic talking about this!
I apologize for my english, but it isn't my mother tongue...

---

