---
title: "Dell inspiron 1300 wireless not working"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by theryanproject0195 on 2014-03-19
Hi. I am trying to install Ubuntu 12.04LTS on a Dell Inspiron 1300. My issue is that the internal wireless card does not work. I tried uninstalling the bcmwl kernel source, and only after receiving it through updates. Every time I try to uninstall it the computer permanently hangs, and the process never stops having the file open even after rebooting. I also tried the fwcutter driver. I believe it is a Broadcom bcm4318. I can get it display the card and just say disconnected, but then when I try to unplug my external Alfa wireless adapter (what I have been using for wireless), the bcm4318 card goes away. If anyone knows the solution, thank you very much.

Ryan

The Ryan Project 01950

---

### Post by Hadaka on 2014-03-19
hi, i have the exact machine and card here.
this is how to get the b43 firmware to load.
open a terminal...ctrl/alt/t and enter..
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
edit the end of the file...as in..add this one line to the end of the file
then,,save and close gedit
```
blacklist b43
```
back to the terminal..please do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
once that loads...then gedit /etc/modprobe.d/blacklist.conf
and REMOVE the one line you added.save and close gedit
open a terminal
then do..
```
sudo modprobe b43
```

---

### Post by theryanproject0195 on 2014-03-20
My 1300 doesn't even show the wireless card when I do that. I have gotten it to display the card though, just no connectivity.

---

### Post by Hadaka on 2014-03-20
ok, then please post the output of,,
```
lspci -nnk | grep -iA2 net
```
thanks.

---

### Post by theryanproject0195 on 2014-03-20
```

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
Subsystem: Dell Device [1028:01c9]
Kernel modules: b44
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
Kernel modules: ssb

```

---

### Post by Hadaka on 2014-03-20
bcmwl kernel source  is the WRONG driver for your card//[14e4:4318]
say NO or ignore when you are offered a driver from additional drivers.
yes..it offers..but NO its the wrong driver....please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe -rf wl
```
then do.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```

---

### Post by theryanproject0195 on 2014-03-21
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
returned "No such file or directory"

and

sudo modprobe -rf wl
returned FATAL: Module wl not found

Should I install available updates? Also, the internal card appears but says disconnected.

---

### Post by theryanproject0195 on 2014-03-21
Thanks for all your help. I fixed it by installing wicd and setting wlan1 as my wireless interface device.

---

### Post by Hadaka on 2014-03-21
glad you got it working !!
please mark solved   how to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

