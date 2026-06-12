---
title: "driver"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Drenriza on 2010-02-03
Is it possible to update drivers for
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

in linux?

Thanks on advance
kind regards

---

### Post by Paqman on 2010-02-03
The Intel graphics drivers are open source, and part of the actual Linux kernel itself. So updates come through with the kernel updates.

What kernel are you running? Open a terminal and enter this to find out:
```
uname -r
```

---

### Post by Drenriza on 2010-02-03
Im running 2.6.24-26-generic

Because its seems to be able to run with vm-ware that ubuntu 9.10 karmic koala is not (without crashes, performance issues, and more)

But as i remember the ubuntu 8.10 version is stable, and able to run vmware. Is it possible to dist upgrade from 8.04 -> 8.10?

And will this help my intel driver program?

---

### Post by Drenriza on 2010-02-03
Bump

---

