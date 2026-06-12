---
title: "Issues with USB-Ethernet adapter"
date: 2016-09-13
forum: Networking &amp; Wireless
---

### Post by jsaarinen on 2016-09-13
Hi everybody,
I'm trying to get ethernet working on a Ubuntu tablet with a USB-ethernet adapter. However, "ifconfig" doesn't show the ethX interface. Should the adapter work at all? Does the kernel include the required driver for the adapter?


Jyrki

---

### Post by jsaarinen on 2016-09-13
The tablet is "[h=2]BQ Aquaris M10 Ubuntu Edition"[/h]

---

### Post by Bucky Ball on 2016-09-13
*Thread moved to **Networking and Wireless**.*

Welcome. Better chance of support here.

Please open a terminal and run these three commands:

```
sudo lshw -C network
iwconfig
lsusb
```

Post the output here between code tags, please. (See the green link in my signature for how.) Which release and flavour of Ubuntu are you running?

```
lsb_release -a
uname -r
```

---

