---
title: "Ubuntu slow connection to router following 14.04 upgrade on 2.4GHz only"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by shaansweb on 2014-08-02
My router broadcasts both a 2.4 GHz signal and a 5 GHz signal. Following an update of my computer to Ubuntu 14.04, my computer has poor connection with my router's 2.4 GHz signal. The speed is slow, even when right next to it, and the connection drops frequently at ranges it used to handle. Connection to the 5 GHz signal seems to work without issues. When I boot from a 13.10 live usb, the connection is fine. However, when I boot from a 14.04 live usb, all the same symptoms occur. This shows the issue is being caused by some change to ubuntu.

Can somebody go about guiding me on how to go about diagnosing and correcting the issue? I can post the output of any terminal commands that might help figure out what's going on.

---

### Post by praseodym on 2014-08-02
Hi,

please show the outputs of 14.04 of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
```

---

