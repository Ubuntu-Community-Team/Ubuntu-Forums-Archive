---
title: "Switch to 64-bit, now ndiswrapper doesn't work"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by malfist on 2008-06-17
I have a NetGear WG111v2 that relies on ndiswrapper for stable performance. If I use the rtl8187 driver, I get less than 1/2 of my max bandwidth and it often drops even lower and I can only use it for about 1/2 hour until it drops connection and will not reconnect until I reboot.

The only driver I was able to get working with ndiswrapper was the initial release driver for 98 (the rest are packaged inside exe's), the 2000, ME, and XP drivers do not work for some reason. Now ndiswrapper complains in dmesg about me using a 32 bit driver for a 64 bit kernel. Is there a work around or has anyone got the WG111v2 working with a 64 bit OS?

Thanks,
Malfist

P.S. The drivers beyond WIN98 support 64-bit but they don't work.

---

