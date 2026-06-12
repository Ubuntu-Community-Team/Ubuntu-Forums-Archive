---
title: "Linksys WMP300N Disconnets 13.10"
date: 2013-11-25
forum: Networking &amp; Wireless
---

### Post by petegregar on 2013-11-25
I have the latest Ubuntu installed.
Linksys WMP300N will connect and seems to work ok for 15min or so.
Then disconnects and will not reconnect until I reboot.

I am using the proprietary drivers.

---

### Post by praseodym on 2013-11-26
Lets check:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
iwlist chan
cat /etc/resolv.conf
sudo iwlist scan
```

---

