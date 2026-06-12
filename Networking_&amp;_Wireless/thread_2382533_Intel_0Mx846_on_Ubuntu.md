---
title: "Intel 0Mx846 on Ubuntu"
date: 2018-01-14
forum: Networking &amp; Wireless
---

### Post by alex495 on 2018-01-14
Hello,
I have an old Intel 1525 laptop with a 0Mx846 wireless adapter. I'm trying to get it working under Ubuntu 16.04, so far without success. I tried using ndiswrapper, loading the bcmwl5 driver into it, and *ndiswrapper -l* lists the driver as installed and device as present. However, no networking. Any ideas about how I can fix this? Any logs I can check, etc.? Thanks in advance.

---

### Post by chili555 on 2018-01-14
Please run and post the result of these terminal commands:```
lspci -nnk | grep 0280
ndiswrapper -l
```

---

### Post by alex495 on 2018-01-14
Ran
```
lspci -nnk | grep 0280
```
Result
```
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
```
Ran
```
ndiswrapper -l
```
Result```

bcmwl5 : driver installed
    device (14E4:4328) present (alternate driver: ssb)
```

---

### Post by chili555 on 2018-01-14
With a temporary working internet connection by ethernet, tethered or whatever means possible, open a terminal and do:```
sudo apt-get install firmware-b43-installer
sudo apt-get purge ndiswrapper*
```Reboot and tell us if the wireless is working.

---

### Post by alex495 on 2018-01-14
Indeed, it's working! So to clarify, what that did was to install a general Broadcomm driver and got rid of ndiswrapper which would otherwise have superceded it? Good knowledge for the future. Thanks so much for helping.

---

### Post by chili555 on 2018-01-14
Some poor chump worked for years to explain all this. Check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

ndiswrapper is usually a last-ditch crutch. I haven't seen it work correctly in several years.

---

### Post by alex495 on 2018-01-14
Your efforts are truly appreciated! Thanks again.

---

