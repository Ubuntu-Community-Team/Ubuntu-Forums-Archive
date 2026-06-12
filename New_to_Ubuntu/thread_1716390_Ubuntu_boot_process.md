---
title: "Ubuntu boot process"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by Bob99 on 2011-03-28
I am fairly new to Ubuntu and am trying to understand the boot process. From what I can understand, the boot process was changed from "the normal SysV boot process system of scripts" to something called "Upstart". The specific method used by "Upstart" seems to vary by distribution. Can somebody please point me to some documentation relative to Ubuntu 10.10.

---

### Post by Rubi1200 on 2011-03-28
As far as I know, Upstart only controls certain processes but not all:
[http://upstart.ubuntu.com/index.html](http://upstart.ubuntu.com/index.html)

For other processes, see the regular System-V init scripts.

This will show you the processes controlled by Upstart:
```
initctl list
```

---

