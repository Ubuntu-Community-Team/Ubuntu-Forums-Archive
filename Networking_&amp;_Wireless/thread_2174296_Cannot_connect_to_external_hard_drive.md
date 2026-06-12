---
title: "Cannot connect to external hard drive"
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by tajreed on 2013-09-13
I have a WD external hard drive connected via USB to a Asus router. My PC connects to the internet through the same router. But Ubuntu 12.04 cannot "see" the external hard drive via the network. Anyone know how to configure Ubuntu so that I can access the hard drive?

---

### Post by sudodus on 2013-09-14
I think there should be an instruction how to do it in the manual for the Asus router. If your paper manual is gone, you can probably find one via the internet. It might also be visible in a menu of the router. I guess you need to know what address it is and what protocol/software you should use to connect.

Do you connect to it from Windows computers? In that case maybe samba can be used.

---

### Post by tajreed on 2013-09-14
Can't figure out Samba nor the router. I contacted ASUS support.

---

### Post by stretch2 on 2013-09-14
It is definitely a setting on the router ... Basically, the router will set it up as a shared drive ... And then you have to map to it.

You may have to format the HDD to ext or FAT rather than NTFS, because I have had some incompatibility sometimes with NTFS on Linux systems (Which I can probably guarantee  your router is using)

Hope this helps :D

---

