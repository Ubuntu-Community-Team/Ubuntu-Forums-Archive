---
title: "Cant get rosewill rnx-N150 to install."
date: 2017-08-08
forum: Networking &amp; Wireless
---

### Post by srobison62 on 2017-08-08
So I've been trying to install the drivers for my N150 but it doesnt like any of the drivers I have tried.  Ive tried googling and people mention some sort of guide, but I haven't been able to find it.  Any help would be great!

---

### Post by praseodym on 2017-08-09
Lets check the terminal outputs from these commands:
```
uname -a
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

