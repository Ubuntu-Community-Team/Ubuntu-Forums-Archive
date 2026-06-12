---
title: "D-Link DWL-G132 usb adapter problem"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by wmlife on 2007-03-14
I am using Kubuntu 6.10 edgy on a i386 machine, and cannot install the usb adapter. I did some research in the forum, and followed the instruction in the post [http://ubuntuforums.org/showthread.php?p=1993115](http://ubuntuforums.org/showthread.php?p=1993115). But it didn't work for me.

I tried the latest ndiswrapper as well as the one from ubuntu repository. I also tried the windows driver coming with this adapter and the latest one downloaded from d-link website. The drivers seem to be installed allright. I saw words like "neta5agu: driver present; device 2001:3A03 present". However, NONE of them worked, and there is no wlan0 if I typed "sudo iwconfig".

I also blacklist the madwifi as some post said the default madwifi only works with pci card.

Does someone solve similar problem before? Any help is appreciated.

PS: the adapter works under WindowsXP.

---

### Post by n00b@linux on 2007-03-15
```
sudo ifconfig wlan0 up
```

---

### Post by wmlife on 2007-03-16
Thanks for the reply. But my problem is that wlan0 device does not exist in my system. I got a "no such device" warning when typing "sudo ifconfig wlan0 up".

---

### Post by n00b@linux on 2007-03-16
Have you loaded ndiswrapper into the kernel?```
modprobe ndiswrapper
```

---

### Post by wmlife on 2007-03-17
I did 'modprobe ndiswrapper'. I checked the start-up message by dmesg, and found it said "windows driver cannot initialize the hardware".

---

