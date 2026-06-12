---
title: "Pickit 2 not found by pk2cmd"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by brian_hughes45 on 2010-11-10
Has anyone had any experience of the Pickit 2 PIC programmer. I'm trying to connect using pk2cmd, but it resolutely comes up with  Pickit 2 not found. lsusb recognises the device, I've got an entry in /etc/udev/rules.d, (SYSFS{idVendor}=="04d8", SYSFS{idProduct}=="0033", MODE="0660"), GROUP="microchip"and I can make an entry appear in /dev/bus/usb/002. I'm obviously very new to this corner of the system- does anyone know where pk2cmd looks for the device, and exactly what it should find?

---

