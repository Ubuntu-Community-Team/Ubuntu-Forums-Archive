---
title: "Accessing Exteranl USB drive in Terminal"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by cquigley on 2009-08-01
Hi Everyone-
 
  I am trying to access my external hdd in the terminal. 
 
When I go into the command line I type "cd /media"
 
Then I typed "ls" to see my options.  My options are the following drives "DATA disk Iomega HDD"
 
""DATA and "disk" are the internal harddrive. When I type "cd" and DATA or disk, is works just fine, I can access the drive.
 
However when I type "cd Iomega HDD" it says it does not exist. I tried every variation "cd /Iomega HDD" , caps and lower case, and still nothing.
 
I can access the drive the GUI interface, but not the terminal. Is there something I need to do before this or what. Any help would be greatly appreciated.
 
Thanks,
  cquigley

---

### Post by Crafty Kisses on 2009-08-01
Run this command as root, what are the results?
```
fdisk -l
```

---

### Post by cosine352 on 2009-08-01
try 
> cd Iomega\ HDD

This is because of the space.

---

### Post by magh-87 on 2009-08-01
You should also be able to select it from a drop down list from Places -> Iomega HDD

Does the external not to auto mount?

---

### Post by cquigley on 2009-08-01
**This is the reponse I get from the terminal**
 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5c5e607
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020        5394    35142187+   7  HPFS/NTFS
/dev/sda3            5395        9403    32202292+   7  HPFS/NTFS
/dev/sda4            9404        9729     2618595    5  Extended
/dev/sda5            9404        9707     2441848+  83  Linux
/dev/sda6            9708        9729      176683+  82  Linux swap / Solaris
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbce2081
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      108853   874360001    7  HPFS/NTFS
/dev/sdb2          108853      121602   102400000    6  FAT16
[EMAIL="cquigley@cquigley-laptop:/media$"]cquigley@cquigley-laptop:/media$[/EMAIL] 
 
**It reads both drives. the 80 gig is the internal and the 1 terabyte is the external.**
 
**thanks,**
**  cquigley**

---

### Post by cquigley on 2009-08-01
Forget my last post. 
 
I didn't see cosine352 response. Thanks so much cosine, got it to work.
 
Thanks to everyone else as well.
 
cquigley

---

