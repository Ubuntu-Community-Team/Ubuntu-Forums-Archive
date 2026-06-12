---
title: "Wireless radio won't turn on on 13.10"
date: 2014-01-08
forum: Networking &amp; Wireless
---

### Post by info20 on 2014-01-08
Wireless radio won't engage. Box is using BCM43228 Chipset and all updates are current through 1/7/14. Any suggestions on a script the might get the wireless card working?

---

### Post by praseodym on 2014-01-08
Hi,

please show the terminal 8CTRL+ALT+T) outputs of these commands:
```
uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
What kind of computer is it? Does LAN work?

---

