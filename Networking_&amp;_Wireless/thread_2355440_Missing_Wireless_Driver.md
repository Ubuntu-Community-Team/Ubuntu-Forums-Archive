---
title: "Missing Wireless Driver"
date: 2017-03-12
forum: Networking &amp; Wireless
---

### Post by mosure2464 on 2017-03-12
I am new to Ubuntu and think I removed my wireless driver after installing. I installed Ubuntu 14.4 LTS on my HP Mini. I'm trying to get the correct wireless driver. When I run lspci I get the following information; Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01) HP Company U98z049  wireless mini PCIe card [103c:1507]. Kernel driver in use : b43-pci-bridge.
I downloaded to my Mini using Ethernet connection Utility for extracting Broadcom 43xx firmware and installed it.  It also downloaded Broadcom 802.11 Linux STA wireless driver source bcmwl-kernel-source, not sure this is the correct one.  Can anyone confirm or deny this for me?  If confirmed, it asks for CD/DVD 'Ubuntu 14.40.5 LTS/Trusty Tahr/-Release i386 (20160803)' is required.  Thank you in advance for any help you can give me.

---

### Post by westie457 on 2017-03-12
Hello and welcome to the Forum.

Please connect the ethernet cable run the following commands one at a time in a terminal. ```
sudo apt remove --purge bcmwl-kernel-source
sudo apt install --reinstall firmware-b43-installer
sudo modprobe -rfv wl
sudo modprobe -rfv b43
sudo modprobe b43
```
Ignore any errors and warnings of something not found or not in use.
After waiting a few seconds unplug the cable then check if wifi is now enabled.
If nothing showing reboot. all should now be working.

Most of the information came from here. [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

