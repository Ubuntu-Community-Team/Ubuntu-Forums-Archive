---
title: "wifi connectivity problem"
date: 2013-09-22
forum: Networking &amp; Wireless
---

### Post by kandukuri_girish on 2013-09-22
i am using 12.04 LTS, 
not able to connect to the wifi from the system..
somebody please help me...

---

### Post by praseodym on 2013-09-22
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```
Does LAN work? What kind of computer is it?

---

