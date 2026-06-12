---
title: "Bluetooth Manager messed up my bluetooth..."
date: 2016-01-03
forum: Networking &amp; Wireless
---

### Post by pingaan on 2016-01-03
Hi,

I wanted to try out Bluetooth Manager, for enhanced BT options. It didn't seem to work for Ubuntu 15.04. Nothing was clickable so I uninstalled it. Now that is done and my BT is no more.
I can't activate my BT anymore. 
How do I reinstall the BT drivers and would that solve the problems? There seem to be crash files concerning pulseaudio as well. The BT device I wanted to enhance was a headset... :(

Regards.

---

### Post by jeremy31 on 2016-01-04
Please post the terminal output for ```
lspci -nnk | grep -iA2 net; lsusb; dmesg | egrep -i 'blue|firm'; rfkill list all
```

---

### Post by pingaan on 2016-01-21
A few reboots later and it seems to have sorted itself out... Thanks anyways!

---

