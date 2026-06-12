---
title: "Screen resolution/SiS graphics card"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by liam____ on 2009-06-14
Dear all,

I am a beginner to ubuntu but already a big fan!

I have recently installed Jaunty 9.04 (32-bit) on my laptop (Fujitsu Siemens Esprimo Mobile, Intel Core2 Duo) but cannot get a screen resolution above 800x600. I know this is a fairly common problem and have read through many of the threads, but can't get anything to work on my system. 

For information, the lspci | grep VGA command returns:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

and my xorg.conf file looks like this:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

I know others have had problems with SiS graphics cards and I have looked into editing the xorg.conf file, but don't really know where to start, although my xorg.conf looks pretty small.

Any help would be gratefully received, I don't want to have to revert to Windows! If any more information is needed, please ask.

Thanks in anticipation,

Liam

---

### Post by liam____ on 2009-06-14
I've fixed it now using the SiS driver provided by **bgerlich** on this thread:
[http://ubuntuforums.org/showthread.php?p=6983046#post6983046](http://ubuntuforums.org/showthread.php?p=6983046#post6983046)
Many thanks to anyone who considered my post.
Liam

---

