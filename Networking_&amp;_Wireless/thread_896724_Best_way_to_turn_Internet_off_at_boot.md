---
title: "Best way to turn Internet off at boot?"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by scu-ba-de-buntu on 2008-08-21
What is the best way to ensure that my computer does not have wireless or Ethernet on from boot until I tell it to? I have multiple networking devices.

Thanks.

---

### Post by Iowan on 2008-08-21
Edit **/etc/network/interfaces** file and delete (or comment out) the "auto" line for interface(s).

---

### Post by scu-ba-de-buntu on 2008-09-03
Thanks for the suggestion, but that does not work. Is there good documentations somewhere on boot-time in Ubuntu, something like rc.0?

---

