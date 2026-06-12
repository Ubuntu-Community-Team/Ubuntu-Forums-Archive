---
title: "BCM4311 Broadcom drivers help"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by deviations on 2008-09-14
I'm trying to use the broadcom drivers in the sticky, but I cant seem to make the file. In the readme, it says 

```
Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

```

my kernel folder says 2.6.24-16-generic, so i type:

make -C /lib/modules/<2.6.24-16-generic>/build M=`pwd` into the terminal, but it says bash: 2.6.24-16-generic: No such file or directory. What am I doing wrong?

---

### Post by Kralizec on 2008-09-15
Try removing the <>'s

---

