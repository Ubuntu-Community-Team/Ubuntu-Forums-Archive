---
title: "Wireless"
date: 2014-05-29
forum: Networking &amp; Wireless
---

### Post by indodwi on 2014-05-29
Hello everyone. I have an annoying problem with wireless on xubuntu. Sometimes the wireless is not connected. I used xubuntu 14.04 on my acer travelmate 2480. Are you have the same problem also? How to fix it? Thanks...

---

### Post by praseodym on 2014-05-29
Hi,

please pen a terminal with CTRL+ALT+T and show the outputs of these commands:
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
```

---

