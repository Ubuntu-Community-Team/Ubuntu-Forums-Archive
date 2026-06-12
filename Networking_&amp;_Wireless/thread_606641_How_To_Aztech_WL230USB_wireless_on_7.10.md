---
title: "How To: Aztech WL230USB wireless on 7.10"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by morpheus5 on 2007-11-08
I've discovered that Aztech Wl230USB is actually based on ZD1211B chipset. It is 100% compliant and tested(by me) 
1. Download "build-essentials", and "linux-source" for compiling.
2. Alt+F2 and type in "gksu gedit /usr/src/linux/drivers/net/wireless/zd_usb.c"
3. add in { USB_DEVICE(0x0cde, 0x001a), .driver_info = DEVICE_ZD1211B }, under /* ZD1211B */
that's device ID for the WL230USB. If you are too lazy to edit the code, i attached a file to it, u can use that to replace /usr/src/linux/drivers/net/wireless/zd1211rw/zd_usb.c
4. in terminal, type "cd /usr/src/linux"
5. type make modules & modules_install
6. reboot

ps. kernel developer pls update the kernel.

---

### Post by sundait on 2007-12-17
Hello morpheus5..

Just curious if you did test them for packet injection in aireplay? If so, is it works?

TIA.

---

