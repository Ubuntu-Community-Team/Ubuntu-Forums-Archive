---
title: "ubuntu 14.04 LTS - Connects to wifi but no internet"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by dilipv105 on 2014-05-24
hi,

i recently installed ubuntu 14.04 and i am having problems connecting to internet via wifi.
 my systems connects to the wifi but it's not able to access the internet.

i tried connecting directly with LAN cable, it works - not sure what's the problem while accessing through wifi, please help.

---

### Post by praseodym on 2014-05-25
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
cat /etc/resolv.conf
ifconfig -a
```

---

