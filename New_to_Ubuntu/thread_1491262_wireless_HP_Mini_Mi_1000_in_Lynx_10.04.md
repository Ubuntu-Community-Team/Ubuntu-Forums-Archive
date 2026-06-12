---
title: "wireless HP Mini Mi 1000 in Lynx 10.04"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by aspergerian on 2010-05-23
After loading Lynx, ethernet connected but wireless did not. Found an efficient solution here:
[http://blog.technicallyworks.com/2009/10/getting-hp-mini-1000-wireless-to-work.html](http://blog.technicallyworks.com/2009/10/getting-hp-mini-1000-wireless-to-work.html)

"launch Synaptic and search for "broadcom". The first result in the filtered list was bcmwl-kernel-source"

Worked for me too.

---

### Post by cariboo on 2010-05-23
All I did was go to System->Administration->Hardware Drivers, and install the restricted Broadcom wl driver. You need an internet connection to install it though.

---

### Post by aspergerian on 2010-05-23
Was your success on an HP Mini 1000?

> **cariboo907 said:**
> All I did was go to System->Administration->Hardware Drivers, and install the restricted Broadcom wl driver. You need an internet connection to install it though.

---

