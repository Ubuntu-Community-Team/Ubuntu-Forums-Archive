---
title: "Wireless Doesn't Work"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by GiovaniMars on 2009-11-10
I been trying to look how to fix it but I can't get my wireless to work. I'm Dual Booting Windows and Ubuntu, so I can use the internet on Windows.  Here is my Wireless Card:
```
Broadcom 802.11b/g WLAN
```

If anyone can help me get my wireless working please post a reply.:D

---

### Post by lavinog on 2009-11-10
please post the output of
```
lspci
```

Many broadcom chips do not allow the firmware to be packaged with ubuntu.  You may need to use a wired connection, then run the hardware manager...It should detect your card and download the firmware for you.

---

### Post by mrboojive on 2009-11-10
Have you tried installing a restricted driver? Go to System > Administration > Hardware Drivers and see if there are any wireless drivers listed.

If not, try installing the package bcmwl-kernel-source using Synaptic or from the command line by doing ```
sudo apt-get install bcmwl-kernel-source
``` Then see if anything shows up in Hardware Drivers.

---

