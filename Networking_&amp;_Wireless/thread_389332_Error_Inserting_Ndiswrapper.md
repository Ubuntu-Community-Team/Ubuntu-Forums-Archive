---
title: "Error Inserting Ndiswrapper"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by nathanhillinbl on 2007-03-20
ok, i've been having ndiswrapper problems, and the previous thread had about 3 of them in it, but i get this error this time:
  sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

All this is confusing me, and its a little discouraging.

---

### Post by tomiu on 2007-03-20
> **nathanhillinbl said:**
> ok, i've been having ndiswrapper problems, and the previous thread had about 3 of them in it, but i get this error this time:
  sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

All this is confusing me, and its a little discouraging.

did u install the driver before u writte:  

sudo modprobe ndiswrapper

---

### Post by nathanhillinbl on 2007-03-20
yea, there are 3 of them, all installed for my linksys wmp11 v4. This is begining to turn into a bit of a pain in the a$$.

---

### Post by JengaBlocks on 2007-03-26
I hit the same problem on the modprobe after rebuilding ndiswrapper and attempting to get a linksys wmp54g wireless card working

---

