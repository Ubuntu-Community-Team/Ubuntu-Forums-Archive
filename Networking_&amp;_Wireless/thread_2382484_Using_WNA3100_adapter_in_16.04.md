---
title: "Using WNA3100 adapter in 16.04"
date: 2018-01-14
forum: Networking &amp; Wireless
---

### Post by alex495 on 2018-01-14
Hello,
I have a bit of a problem in getting my (rather old) WNA3100 netgear wireless adapter to work with a laptop running Ubuntu 16.04 LTS 64-bit. I installed ndiswrapper and loaded it up with the latest netgear driver (bcmwlhigh6). Running ```
ndiswrapper -l
``` indicates that the driver is installed and the device is present. However, running ```
iwconfig
``` shows no wireless extensions, and I don't see any option to connect to wifi from the GUI. I ran the required commands sudo depmod -l(*sudo modprobe ndiswrapper* and *sudo ndiswrapper -m*) and rebooted several times to no avail. I'm pretty new to Linux so I don't know how to troubleshoot this further on my own. Any suggestions would be greatly appreciated.

---

### Post by chili555 on 2018-01-14
Please see: [https://ubuntuforums.org/showthread.php?t=2264020&highlight=wna3100](https://ubuntuforums.org/showthread.php?t=2264020&highlight=wna3100)> I don't believe this device can be made to work correctly in Ubuntu 14.04 and later. Please don't ask me to help. I've tried everything I know of and it doesn't work.


---

### Post by alex495 on 2018-01-14
Thank you for your reply. I'm currently trying a different route and also have an issue, but I'll make a new thread for that.

---

