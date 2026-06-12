---
title: "wireless fun"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by needy on 2007-03-07
I'm running Edgy with 6.11 kernel.  I have a Netgear wg111v2 USB wireless dongle.   I'm using ndiswrapper 1.8.  The wireless works fine until I reboot the system.  If I reboot, remove the dongle, log back in, and then insert the dongle; the wireless will work without problems.  If I reboot with the dongle in the USB slot, the wireless won't work.  I looked through dmesg and I noticed that a rtl8187 driver loaded.  I had already added rtl8187 to /etc/modprobe.d/blacklist, but I'm guessing that the blacklist doesn't prevent the kernel from loading the driver during bootup.

How do I make sure that the ndiswrapper driver loads instead of rtl8187?

---

### Post by chili555 on 2007-03-07
Try ```
blacklist  r8187
``` and see if that does it.

---

### Post by needy on 2007-03-07
It worked.

Thanks

---

