---
title: "UtechSmart USB Bluetooth 4.0 USB dongle"
date: 2014-10-22
forum: Networking &amp; Wireless
---

### Post by ngant on 2014-10-22
I just bought a new (Broadcom BCM20702 chipset) UtechSmart USB Bluetooth dongle for my Linux Ubuntu laptop running 14.04 LTS.  Haven't got any recognition from the laptop when inserted in the USB slot.  Vendor states compatible with "Linux kernels 3.6.11-4 and higher", but I can get it to work.  Any drivers to pull out of Unity's Software Center?

---

### Post by praseodym on 2014-10-22
Please open a terminal with CTRL+ALT+T and show the outputs of:
```

lspci -nnk
lsusb
lsmod
dmesg | grep Blue
```

---

