---
title: "Ethernet module not being associated. Help"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by raul_ on 2007-07-27
This isn't a Ubuntu question, but I think it's universal. I bought a new laptop and I'm dying to install Linux (actually it's installed). The only problem is that my ethernet card module is not being associated.

When I type "lsmod" , the module is there, but there is a 0 in front of it, which means it's not being associated. How do I manually tell r8160 to be associated with eth0?

---

### Post by noob12 on 2007-07-27
Can we step back a bit.  Please post the output of
> 
lshw -C network

It will tell us the chipset and current driver association.

---

