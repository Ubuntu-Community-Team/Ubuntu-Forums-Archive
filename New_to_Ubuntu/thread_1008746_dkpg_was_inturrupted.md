---
title: "dkpg was inturrupted?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Acavando on 2008-12-11
i was trying to download adobe flash with synaptics and got

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i cant run any installer whatso ever? how do i fix it?

---

### Post by OutOfReach on 2008-12-11
It says right there. :)

Run:
```

sudo dpkg --configure -a

```
In a terminal.

---

