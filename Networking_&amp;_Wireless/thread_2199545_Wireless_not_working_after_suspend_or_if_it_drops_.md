---
title: "Wireless not working after suspend or if it drops for any other reason"
date: 2014-01-14
forum: Networking &amp; Wireless
---

### Post by thorsten_niehues on 2014-01-14
On Ubuntu 12.04 the wireless network drops occasionally if that happens I can not get it back again (except for reboot)
The same problem exists if I suspend the laptop

If I try > ifconfig wlan0 down
> ifconfig wlan0 up
I get
SIOCSIFFLAGS: Input/output error

any suggestions?

---

### Post by praseodym on 2014-01-16
Lets check the hardware and settings:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
```

---

