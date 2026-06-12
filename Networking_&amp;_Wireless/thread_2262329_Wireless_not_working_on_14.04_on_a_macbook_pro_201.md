---
title: "Wireless not working on 14.04 on a macbook pro 2011"
date: 2015-01-24
forum: Networking &amp; Wireless
---

### Post by jesper9 on 2015-01-24
Hello,

I'm new to ubuntu and I'm in desperate need of assistance.
My wlan doesnt work and I looked around forums and found no solution that worked for me. 


This is my broadcom device (used code 
lspci -nn | grep 0280):
Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)

Any ideas?

---

### Post by Hadaka on 2015-01-24
Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

---

### Post by jesper9 on 2015-01-24
> **Hadaka said:**
> Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

Hi,

Thank you for the qucik reply. It didn't work, couldn't find the package 
bcmwl-kernel-source

Any other tricks? =)

---

### Post by jesper9 on 2015-01-24
> **Hadaka said:**
> Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

And now it works. Thank You very much =)

---

### Post by Hadaka on 2015-01-24
Great !
glad that worked for you.

---

