---
title: "[SOLVED] Ntop and wireless"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by wormser on 2007-06-20
Ntop works fine with my ethernet adapter but I cannot get it to work with my wifi adapter.  I do not see anything in /var/lib/dpkg/info/ntop.config to change the adapter.  It is a bit confusing so it might be there.

Thanks

---

### Post by wormser on 2007-06-23
Any ideas?  Thanks.

---

### Post by wormser on 2007-07-30
bump

---

### Post by wormser on 2007-08-25
Resolved it.

The file is here:  /var/lib/ntop/init.cfg

```
sudo nano /var/lib/ntop/init.cfg
```

Then edit this line: INTERFACES="eth0","eth1"
I added eth1 for my wireless card and it is working.

---

