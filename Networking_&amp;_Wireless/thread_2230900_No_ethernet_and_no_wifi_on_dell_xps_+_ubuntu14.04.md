---
title: "No ethernet and no wifi on dell xps + ubuntu14.04"
date: 2014-06-21
forum: Networking &amp; Wireless
---

### Post by prasad9 on 2014-06-21
Hi,

I am new to linux and just installed ubuntu 14.04 on my dell xps which had windows vista earlier. Before installation, I had wifi connectivity. I had to go to Software & updates --> Additional drivers and chose BroadCom Corp Wireless 1397 WLAN mini-card. But after installation and selecting all default options, I am not able to connect to wi-fi or ethernet. Ethernet dhcp is not working. I tried giving manual addresses and it says connected but there is no internet connectivity. 
Any help is greatly appreciated.

---

### Post by praseodym on 2014-06-22
Hi,

please show the terminal outputs of
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
```

---

