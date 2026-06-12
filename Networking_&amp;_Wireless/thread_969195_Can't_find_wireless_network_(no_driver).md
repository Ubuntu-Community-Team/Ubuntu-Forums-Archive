---
title: "Can't find wireless network (no driver?)"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by MoscowModder on 2008-11-03
Hey everyone, I'm pretty new to Ubuntu (and Linux in general).
I'm using WUBI to run Ubuntu 8.10 Intrepid Ibex on Windows XP Professional.
On Ubuntu no wireless networks are recognised, and on Windows (and my other computers) it works fine.  I think I'm missing the wireless driver.  Does anyone know where to find it (I heard somewhere about installing a Windows driver) or how to enable it?

---

### Post by superprash2003 on 2008-11-03
try system->admin->hardware drivers.. if you still have problems, post output of lshw -C network

---

### Post by MoscowModder on 2008-11-03
Many thanks!  I tried Hardware Devices, and after connecting physically to the router, it found me the driver.  Wireless now works perfectly.

---

