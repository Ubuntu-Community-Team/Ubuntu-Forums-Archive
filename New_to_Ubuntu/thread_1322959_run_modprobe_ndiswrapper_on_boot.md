---
title: "run modprobe ndiswrapper on boot?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by g3k0 on 2009-11-11
Hey,

quick question. I have to run sudo modprobe ndiswrapper every time I start the computer.  I set it up the way I did previously on 9.4 but it doesn't start automatically now on 9.10.  I did sudo ndiswrapper -m and I manually put it into modprobe.  What am I failing to do?

Thanks

---

### Post by falconindy on 2009-11-11
Add 'ndiswrapper' to /etc/modules.

---

### Post by g3k0 on 2009-11-11
Ah ok. That worked. Thanks

---

