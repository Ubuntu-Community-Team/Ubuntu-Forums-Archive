---
title: "&quot;free -m&quot; not the same as system monitor"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by J V on 2010-01-31
Output of free -m:
```
             total       used       free     shared    buffers     cached
Mem:          2006       1446        559          0         97        702
-/+ buffers/cache:        647       1359
Swap:         1906          0       1906
```System monitor shows 646 of 2 gigs used in ram, 0 of 1.9 gigs in swap.

The swap and buffers/cache lines seem to match up, so what is the mem line doing?

(Probably nothing, just curious)

---

### Post by NightwishFan on 2010-01-31
The top line shows the "total" ram in use. Linux uses empty ram to cache commonly used files for better performance. The second line is the real "used" ram. There is no downside to having your ram be used as a cache, as it will be emptied if another application needs it.

You can see the result of this by opening OpenOffice.org Writer, then closing and reopening it, it should appear much faster because it is in cache.

---

### Post by J V on 2010-01-31
ahh, of course, thought the cache was shown on sys monitor, but this is cool too :)

---

