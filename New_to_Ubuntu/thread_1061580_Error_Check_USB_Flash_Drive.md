---
title: "Error Check USB Flash Drive"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by RealG187 on 2009-02-05
How do I error check (scandisk/chkdsk) a USB drive in Ubuntu?

---

### Post by jerome1232 on 2009-02-06
That depends on the file system. For native linux filesystems you can just run fsck (stands for file system check) which will in turn call the correct file system tool to check the disk for errors. The filesystems must be unmounted to do this.

ie
```
fsck /dev/sda1
```

I know fsck.msdos will check fat16 and fat32 filesystems, 
For ntfs you need ntfsprogs checked and the program ntfsfix can fix very basic errors with ntfs filesystems. Although I'd strongly lean towards using chkdsk from windows when dealing with Microsoft filesystems.

---

### Post by CDrewing on 2010-08-22
Take [h2testw]("http://www.heise.de/software/download/h2testw/50539") & Wine. Thats the best quick & dirty solution for your problem. But at all it is nasty. I have a 32 GByte microSDHC chip here to be tested and it will take the whole evening. :popcorn:

---

