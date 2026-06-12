---
title: "compax mini wireless not active"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by MrNewie on 2013-10-27
Need help getting wireless up & running on a new install of umbutu

---

### Post by Hadaka on 2013-10-27
Hi, Let's get some information and see what transpires.
Please post the output of..
```
lspci -nn | grep 0280
rfkill list all
```
thanks.

---

### Post by MrNewie on 2013-10-28
eric@eric-Compaq-Mini-110c-1100:~$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
eric@eric-Compaq-Mini-110c-1100:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no



right now using a usb plug in but would be nice to have other working

---

### Post by Hadaka on 2013-10-28
thanks.please do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
Remove the USB stick..boot

---

### Post by MrNewie on 2013-10-28
Fixed it Great & Thanks Now in less code terms what exactly did I do?

---

### Post by Hadaka on 2013-10-28
Glad to see its working !!
You loaded the correct driver for your wireless card.
Please click this link and mark your thread solved.
How to-> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

