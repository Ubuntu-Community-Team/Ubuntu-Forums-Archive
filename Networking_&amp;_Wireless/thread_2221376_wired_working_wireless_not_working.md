---
title: "wired working/ wireless not working"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by cicada2 on 2014-05-01
I just installed LUbuntu (Ubuntu14.04.4 LTS) and did the updates from the update manager. I also ran the driver update. This is an older laptop with wireless (worked fine in xp). I don't know where to start to get my wireless connected in LUbuntu. Please be patient as I am a beginner. Any help is greatly appreciated. 

 Compaq Presario-R3000 
Pentium(R)4 - 2.40 GHz

---

### Post by Hadaka on 2014-05-01
Hi, please open a terminal  ctrl/alt/t and enter...
```
lspci -nn -d 14e4:
```
post the output
thanks.

---

### Post by cicada2 on 2014-05-01
cicada@cicada-Presario-R3000-DS514U-ABL:~$ lspci -nn -d 14e4:
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
cicada@cicada-Presario-R3000-DS514U-ABL:~$

---

### Post by Hadaka on 2014-05-01
Hi, from a wired connection to the internet please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
dont be concerned if the above error's out..then do..
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot

---

### Post by cicada2 on 2014-05-02
I decided to try your suggestions once more this morning and I am now up on wireless. Everything looks brighter in the morning! 

Big thanks to Hadaka!!

---

