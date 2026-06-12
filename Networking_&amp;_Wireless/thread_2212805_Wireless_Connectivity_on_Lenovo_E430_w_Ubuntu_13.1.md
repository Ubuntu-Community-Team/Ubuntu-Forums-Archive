---
title: "Wireless Connectivity on Lenovo E430 w/ Ubuntu 13.10"
date: 2014-03-23
forum: Networking &amp; Wireless
---

### Post by r557 on 2014-03-23
I can't seem to connect to any wireless network on this laptop.

It's picking up the wireless networks, but can't ever seem to establish a connection.

Looking for some ideas on how to get this resolved.

---

### Post by praseodym on 2014-03-23
Please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
sudo iwlist scan
rfkill list
cat /etc/resolv.conf
```

---

