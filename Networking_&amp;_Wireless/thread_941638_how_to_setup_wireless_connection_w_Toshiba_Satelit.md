---
title: "how to setup wireless connection w/ Toshiba Satelite L45-S4687 Laptop"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by domingostylez on 2008-10-08
i have a clean setup of ubuntu linux and it is not picking up my wireless card. it will detect the card but it doesnt show it as a wireless connection

---

### Post by Kevbert on 2008-10-08
Welcome to Ubuntu.
You need to tell us what wireless chipset your adapter is based upon.
Go to Applications-Accessories-Terminal and enter the following;
```
lspci
ifconfig
iwconfig
```
You can copy the output of each command by selecting the output and pressing Ctrl-Shift-C to copy and Ctrl-V to paste here.

---

