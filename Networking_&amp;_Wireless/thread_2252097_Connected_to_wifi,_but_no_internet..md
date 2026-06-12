---
title: "Connected to wifi, but no internet."
date: 2014-11-08
forum: Networking &amp; Wireless
---

### Post by Logan_McCarthy on 2014-11-08
Hello, let me start by saying that i'm an Ubuntu noobie. Okay, so i installed Ubuntu onto an old Win XP machine and set it up using Ethernet, then plugged a Wifi adapter into the PC and connected with no problems, about a week later i can still connect but i no longer get internet, i try opening Firefox, the app store, go through terminal and try to install GDParted, but i get nothing.
Thanks for your help!

---

### Post by praseodym on 2014-11-09
Please check the terminal outputs of
```

lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
route -n
ca /etc/resolv.conf
```

---

