---
title: "modprobe: FATAL: Module b43 not found"
date: 2017-10-30
forum: Networking &amp; Wireless
---

### Post by blacksn on 2017-10-30
Im using Ubuntu 16,04 with kernel 4.1 with mmc patch.

I cant get wifi working, I have BCM4318 adapter. I have installed firmware-b43-installer and b43-fwcutter

[    1.700065] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[    1.732174] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[    1.732195] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 8, Version 0
[    1.744449] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[    1.744468] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[    1.744488] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[    1.744505] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[    1.744507] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    1.744514] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    1.744519] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

---

