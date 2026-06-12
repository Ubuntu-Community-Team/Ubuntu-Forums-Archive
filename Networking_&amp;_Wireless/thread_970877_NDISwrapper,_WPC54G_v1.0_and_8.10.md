---
title: "NDISwrapper, WPC54G v1.0 and 8.10"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by two00lbwaster on 2008-11-04
I couldn't get this wireless card to work with the 3.30.15.0 driver at all using NDISwrapper, however, having started using the 3.100.64.0 driver I can get it to connect, something it would never do with the 3.30 driver, but it hard locks the kernal and I have to power off and on again if I try to use the connection.

As I got this same problem but with PCLOS 2007, with the 3.30 driver this time, I'm beginning to think that this might be an NDISwrapper issue.  I have had this card working under NDISwrapper on Ubuntu with the 3.100 driver, but that was using the 7.10 64bit release, but this is not a possibility as this hardware doesn't support 64bit OSes.

Any help would be welcome.

---

### Post by nixscripter on 2008-11-04
Ndiswrapper locking the kernel seems a little unusual. Do you get any information out of /var/log/messages when this happens?

---

