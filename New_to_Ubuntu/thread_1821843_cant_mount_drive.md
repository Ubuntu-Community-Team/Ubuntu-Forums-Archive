---
title: "cant mount drive"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-09
I am having trouble mounting the drive.  

> 
Unable to mount drive
error mounting: mount exited with exit code 18: Failed to open ntfs attribute: No such file or directory
Failed to mount 'dev/sdb1': No such file or directory 

Is there a way to mount it through terminal? Thank you.

---

### Post by 007casper on 2011-08-09
sudo fdsik -l
> 
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc1018db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121576   976559188+  42  SFS
/dev/sdb2          121577      121601      200812+  42  SFS


?

is this corrupted or something?  Why does it say SFS for system?

---

### Post by 007casper on 2011-08-09
bump

---

### Post by amjjawad on 2011-08-09
[http://en.wikipedia.org/wiki/Self-certifying_File_System](http://en.wikipedia.org/wiki/Self-certifying_File_System)

Sorry if I can't help much but try to search here: [www.googlubuntu.com](www.googlubuntu.com)

---

