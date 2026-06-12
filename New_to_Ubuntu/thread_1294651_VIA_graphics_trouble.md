---
title: "VIA graphics trouble"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by siva1086 on 2009-10-18
Hello,

I am almost new to ubuntu having used only jaunty till now. I could find many posts on trouble with VIA graphics card but most of them were for older versions of ubuntu.

After lot of trials, I changed some settings and just want to make sure I did the right thing. My xorg.conf file looks like below:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline "1152x864"    104.99   1152 1196 1324 1552    864  869  872  898 -hsync +vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "Device"
    Driver "via"
    VendorName      "VIA Tech"
    BoardName       "via"
    Identifier    "Configured Video Device"
EndSection

The last entry for Device section was done by me after lot of googling. Is this a valid entry if I want to use the VIA default driver (not S3, not unichrome, not anything else)?

The entry in lspci is thus:
lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

After changing, my system has got faster graphics rendering (which was slow before and therefore the root of all troubles) but I am not sure if I am screwing up something else. BTW, I downloaded all deb packages and installed every driver I could, but I have a feeling that I wasn't able to change the driver till I changed the xorg.conf.

Any help will be greatly appreciated.

Thanks
Siva

---

### Post by halitech on 2009-10-18
everything looks okay to me and if your system is working better then I would say no harm has been done.

---

### Post by siva1086 on 2009-10-19
Thanks Halitech. You made my day.

---

### Post by BikeHelmet on 2009-10-19
I have a similar board. :)

```
bikehelmet@via-Ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

```
I used Ubuntu Tweak to enable the OpenChrome repositories, which have newer drivers in them. That gave me my speed boost. For my board, the default via driver crashes when playing a video.

Congrats!

---

