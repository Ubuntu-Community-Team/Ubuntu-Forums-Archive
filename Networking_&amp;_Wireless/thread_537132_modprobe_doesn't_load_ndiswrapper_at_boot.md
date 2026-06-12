---
title: "modprobe doesn't load ndiswrapper at boot"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by sopordave on 2007-08-28
I can load the driver just fine at the command line by doing

modprobe ndiswrapper

but I would like it to automatically load it when linux boots up.  what do I do?

---

### Post by Zorael on 2007-08-28
I may be wrong, but I believe you'll get it to autostart if you add ndiswrapper to /etc/modules.

```
zorael@azrael:/etc$ cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
**ndiswrapper**
```

Much like so.

---

### Post by sopordave on 2007-08-28
thank you!

---

### Post by jonkulp on 2007-12-09
Awesome!  This worked for me too.  Many thanks.

---

### Post by XeiaieX on 2008-03-11
me three! :mad:

---

