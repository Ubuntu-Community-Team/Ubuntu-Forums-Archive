---
title: "Will having Windows and Ubuntu dual installed..."
date: 2009-12-16
forum: New to Ubuntu
---

### Post by BT1 on 2009-12-16
If I do a dual boot, two different partitions on the same HD, will the windows install fragment files on the other partition, or just the partition it's on?

---

### Post by fancypiper on 2009-12-16
Just the partitions that are NTFS.

---

### Post by Dark_Stang on 2009-12-16
> **fancypiper said:**
> Just the partitions that are NTFS.
Any partition that windows accesses. Be it NTFS, FAT32, FAT16, etc.

---

### Post by lisati on 2009-12-16
> **BT1 said:**
> If I do a dual boot, two different partitions on the same HD, will the windows install fragment files on the other partition, or just the partition it's on?

Only the partitions that Windows has write-access to. As fancypiper points out, this is likely to be the NTFS partitions only. In a basic dual-boot setup, each OS will normally use only its own paritions.

---

### Post by Shazaam on 2009-12-16
Beware installing drivers in Windows so it will have write access to ext2/3/4 partitions. At one time I had seven linux distros installed and Windows kept putting Recycle Bins in each and every one of them. Very annoying.

---

