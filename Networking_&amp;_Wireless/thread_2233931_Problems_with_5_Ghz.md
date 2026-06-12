---
title: "Problems with 5 Ghz"
date: 2014-07-11
forum: Networking &amp; Wireless
---

### Post by Michael_Shakro on 2014-07-11
Hello. I have a TP-link tl-wdn4200 dual band wifi card with the ralink rt3573  chipset. On ubuntu 14.04 the default drivers were the rt2800 which does  not support dual band. I compiled the rt3573 drivers and installed the  module and it seems to be running. The problem is that when It's  connected to 5 ghz, it's incredibly slow. Most of the time websites  refuse to load. I blacklisted the old drivers but I don't know what to  do anymore. Any help would be greatly appreciated.

---

### Post by praseodym on 2014-07-11
Please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
route -n
```

---

### Post by Michael_Shakro on 2014-07-11
I was going through those and I decided to switch channels to see if it would change anything. It was set to channel 165 but when I set it to channel 40 it works fine. This is strange. It doesn't seem to work well with higher channels.

---

### Post by praseodym on 2014-07-12
Maybe a lot of networks around? Check "sudo iwlist scan"

---

