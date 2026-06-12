---
title: "Problem with wireless"
date: 2015-06-01
forum: Networking &amp; Wireless
---

### Post by noidea2 on 2015-06-01
Hi, i instaled lubuntu in a old laptop, toshiba satellite l40-15g .

The problem is that i cant make my wireless card work.

I tried many things that i saw in this forum but noone worked.

Here some info:

[ATTACH]262356[/ATTACH]

Thanks

---

### Post by praseodym on 2015-06-02
Hi,

obviously, you installed the Broadcom-STA driver unnecessarily?!
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
```
Reboot.

---

### Post by noidea2 on 2015-06-02
Thanks, its working :D

---

