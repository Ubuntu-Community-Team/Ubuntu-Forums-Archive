---
title: "Qualcomm Atheros AR922x Wireless Network Adapter failed after 18.04 upgrade"
date: 2018-06-09
forum: Networking &amp; Wireless
---

### Post by hollywoodpete on 2018-06-09
I upgraded my Ubuntu desktop to 18.04 and my wireless card is recognized but does not appear in Network Manager.

[http://paste.ubuntu.com/p/Sf3hWXQ84p/](http://paste.ubuntu.com/p/Sf3hWXQ84p/)

---

### Post by chili555 on 2018-06-09
I'd like to see what's going on, or more likely wrong, on the PCI bus. Please run and post:```
dmesg | grep 03:05
```

---

### Post by hollywoodpete on 2018-06-09
dmesg | grep 03:05
[    0.100138] pci 0000:03:05.0: [168c:ff1d] type 00 class 0x020000
[    0.100161] pci 0000:03:05.0: reg 0x10: [mem 0xfe900000-0xfe90ffff]

---

