---
title: "Broadcom 4311 with Hardware switch"
date: 2015-12-31
forum: Networking &amp; Wireless
---

### Post by wood-raymond79-0 on 2015-12-31
#

---

### Post by chili555 on 2015-12-31
Please remove the incorrect driver for your 4311:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
```Reboot and let us hear the result.

---

