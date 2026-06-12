---
title: "Intel Dual Band Wireless-AC 3160 on Ubuntu 16.04 (64bit)"
date: 2017-08-24
forum: Networking &amp; Wireless
---

### Post by tziulm on 2017-08-24
Hi,

Is the Intel Dual Band Wireless-AC 3160 a good WiFi+Bluetooth card for my Asus X552C? Is it compatible with Ubuntu 16.04? I need to change my  MT7630E because it doesn't work on Ubuntu (there was a patch on github to fix it, but it stopped working after the last kernel updates. Since 4-4-0-87 the system freezed if I tried to install it and I can do nothing about it). I have a double booting  machine, with Windows 8.1 on it as well.

---

### Post by chili555 on 2017-08-24
Please see: [https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html)

The Intel 3160 is fully supported by the driver* iwlwifi *since kernel version 4.1. Ubuntu 16.04 uses 4.4. Verify:```
uname -r
```The device should work perfectly with no extra steps or driver installation needed.

---

### Post by tziulm on 2017-08-25
Great! Thank you very much!

---

