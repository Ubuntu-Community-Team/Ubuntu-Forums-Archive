---
title: "showing a disk that isn't there"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Tm0 on 2008-12-30
hey, I had an sd card in my laptop for a while and left it in there, and all was fine. but one day, when I turned it on, it register 2 cards in it, and when I took it out, it only registered a disk, any way I can fix this?

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11         402     3148740    b  W95 FAT32
/dev/sda3   *         403       14342   111973050   83  Linux
/dev/sda4           14343       14593     2016157+   5  Extended
/dev/sda5           14343       14593     2016126   82  Linux swap/Solaris

here's the fdisk -l output if it helps,oh and this is a preloaded dell laptop if your wondering about the dell utility partition thingy.

---

