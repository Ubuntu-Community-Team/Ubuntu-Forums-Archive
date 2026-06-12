---
title: "problem with wifi and ethernet"
date: 2014-05-29
forum: Networking &amp; Wireless
---

### Post by limner on 2014-05-29
hi
i'm using lubuntu 14.04 trusty
today i was using wifi when during router maintenance i shut down the computer, now the wifi connection refuse to connect.
it does not give me any advice: it find the wifi networks but doesn't connect when i try (and don't give any advice!)

sadly also the ethernet connection does not work (failed at least 1 year ago)

i also tried internet wifi removing password, firewalls and mac filters.....

---

### Post by praseodym on 2014-05-29
[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

Please check this link. If its not enough open a terminal and show the outputs of these commands:
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
route -n
rfkill list
```

---

