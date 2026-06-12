---
title: "Jaunty - Issue with projecting Laptop using VGA"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by shankfree on 2009-05-16
After spending a couple of weeks looking for solutions without success, I'm asking for help!

I have a Thinkpad R51 laptop with Intel Pentium M 1.5 GHz processor, 768 MB RAM; I am running Jaunty on it. I want to project the screen onto a 40" Samsung TV using a VGA cable. I am able to see any static windows (e.g. desktop, text editors, folders, etc.) on the TV, but am not able to see any video. I can see the window frame, but the inside is black on the TV (the laptop screen shows the video fine). I found that the issue was with my xorg.conf file. I edited it as suggested in the forums [here]("https://help.ubuntu.com/community/RadeonDriver#Testing%20The%20Driver"). After that, I was able to see video both on the screen and the TV.

However, a week later (around May 5, '09), Jaunty installed some updates which brought the original problem back. I tried meddling with the xorg.conf file again, but to no avail. Could you please help me resolve this issue? I'd like to see the best image and video on the TV.

I appreciate your time and effort in helping me! Please tell me if I need to include any further information.

Thanks,
Shankara

Here is information that might be relevant:
Intel Pentium M 1.5 GHz processor, 768 MB RAM
Video Card: ATI Radeon Mobility 7500
Method of connecting to TV: VGA cable
TV: 40" Samsung (Model - LNT4061FX)

\etc\X11\xorg.conf file:
**************************
Section "Device"
    Identifier    "Radeon 7500"
    Driver        "ati"
    BusID        "PCI:1:0:0"
    Option        "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Radeon 7500"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
        Virtual        1024 768
    EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option    "Composite" "Enable"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
**************************

---

### Post by coffeeaddict22 on 2009-05-16
Hi,
The obvious glitch is that you've sent the output of xorg.config, not xorg.conf; unless you've got an identical file by the name of xorg.conf, the info in that is of little value... but you could rename it.

---

### Post by shankfree on 2009-05-17
> **coffeeaddict22 said:**
> Hi,
The obvious glitch is that you've sent the output of xorg.config, not xorg.conf; unless you've got an identical file by the name of xorg.conf, the info in that is of little value... but you could rename it.


My mistake...I actually posted the contents of xorg.conf (not "xorg.config"). I don't have a file with the name "xorg.config".

Thanks,
Shankara

---

### Post by shankfree on 2009-05-17
OK..an update...after a few more trials (and errors), I managed to get to a version of the xorg.conf file that allows video display. I modified the "Screen" Section to be the following:
**********

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Radeon 7500"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1920x1080@60" "1024x768" "800x600"
#        Virtual        1024 768
    EndSubSection
EndSection

**********

The TV manual (pdf version available [here]("http://downloadcenter.samsung.com/content/UM/200703/20070301133755718_BN68-01178A-00L02-0216.pdf") on page 46) states that the optimum resolution is 1920x1080 with frequency 60Hz.

I hope this solves the issue. In case you find anything obviously wrong and/or fishy, please recommend appropriate action!

Thanks,
Shankara

---

### Post by cariboo on 2009-05-17
I saw this on the Ubuntu Planet web site, open a terminal and type:

```
xrandr --output VGA --auto
```

---

