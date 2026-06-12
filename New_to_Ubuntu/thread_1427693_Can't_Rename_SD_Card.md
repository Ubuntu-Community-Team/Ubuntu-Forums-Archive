---
title: "Can't Rename SD Card"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by WorldTripping on 2010-03-11
OK, so I bought two SD cards at the same time to put music on.

Both mount fine and both are now full.

fdisk says this:

> 
   Device Boot    Start    End     Blocks      Id  System
/dev/mmcblk0p1    1        1950    15659008    c   W95 FAT32 (LBA)


One I can use mtools to rename, the other I get this error message:

> 
init :: sector size (0) not a small power of two
Cannot initialize '::'
mlabel: Cannot initialize drive


Using the command:
```

sudo mlabel -i /dev/mmcblk0 ::MUSIC_2

```

gParted does not seem to see them, and I followed this guide to renaming:

[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

Anyone any ideas.

Thanks in advance.

---

### Post by WorldTripping on 2010-03-12
Sorted this out.

Formatted the card again and then I could rename it.

---

