---
title: "[SOLVED] Can't change size of partitions"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by kramer65 on 2008-12-08
Hello,

I have to rearrange my partitions a bit since one of them is becoming to small. I sudo started Gparted and it has the button to move/resize partitions. However, I cannot click it when I select any partition except for the swap.

What am I doing wrong here?

---

### Post by geirha on 2008-12-08
Gparted will not alter any partitions if the drive is in use, typically that means you must unmount all filesystems that are on that drive. Gparted will show which partitions are in use by displaying a lock icon on it. You won't be able to unmount the / filesystem so if / is on that drive, you'll need to boot a liveCD to do it. Your ubuntu CD has gparted pre-installed, so just boot that.

EDIT: Oh and please make sure you've backed up all files on that drive that you can't afford to lose. If you suffer a power loss in the middle of the operation for example, you may lose files.

---

### Post by kramer65 on 2008-12-08
Ah ok, that makes sense. 

I just unmounted the drives (they were on an external harddrive) and it is now repartitioning.

Thanks!

---

### Post by gettinoriginal on 2008-12-08
Glad you got it.  Please go to tools and mark this as solved  Thanks

---

