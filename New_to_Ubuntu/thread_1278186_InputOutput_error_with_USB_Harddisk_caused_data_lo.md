---
title: "Input/Output error with USB Harddisk caused data loss!"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by lian1238 on 2009-09-29
Hi all,

Just now, I was moving files from my main harddisk to my external USB one.
The USB plug or the cable was bad and caused an Input/Output Error.
Now everything in the destination folder on the external drive is gone!
How can I recover it? The free space is the same as before the loss, and I lost over 10 GB!

Any help will do! I'm desperate..

---

### Post by ~sHyLoCk~ on 2009-09-29
Check your main hard disk properly to see if the data is still there.

---

### Post by lian1238 on 2009-09-29
I was moving only 3 files to the folder. What happened was everything in the destination folder is gone. PLUS the folder next to that folder. 15GB worth of data...
And I cannot open the drive in Windows (VBox).

---

### Post by lian1238 on 2009-09-29
Here is fsck for that drive:
```

Tue Sep 29 18:45:36 :~$ sudo fsck.vfat /dev/sdc1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/Himum/Season 3
 Start does point to root directory. Deleting dir. 
/Himum/Season 4
 Start does point to root directory. Deleting dir. 
Reclaimed 230786 unused clusters (7562395648 bytes).
Free cluster summary wrong (4099530 vs. really 4330316)
1) Correct
2) Don't correct
? 2
Leaving file system unchanged.
/dev/sdc1: 7263 files, 3298945/7629261 clusters
```

---

