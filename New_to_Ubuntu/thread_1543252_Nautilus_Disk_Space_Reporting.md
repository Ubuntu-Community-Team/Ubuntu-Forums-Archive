---
title: "Nautilus Disk Space Reporting"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by cheetaux on 2010-07-31
I have a 2 TB external harddrive connected in which 1 TB is partitions as a ntfs filesystem and 1 TB is partitioned as a ext4 filesystem.  Currently, no files on on the ext4 partition (there is a lost+found directory).

When I view the external ext4 disk (/media/wdext4) using Nautitus, I see the following:

[ATTACH]165114[/ATTACH]

But doing a df in the terminal, I see:
```
/dev/sdb1            961432072    204436 912389636   1% /media/wdext4
```

Why is Nautilus showing the the drive is about 5% full, but df is showing it 1% full.  Just curious.

---

### Post by mcduck on 2010-07-31
5% of disk space is by default reserved to root user only on Ext filesystems. Since you are viewing the disk stats as normal user that 5% doesn't count as available space.

The reason for the reserved space is to make sure that nornmla users cant accidentally fill the system partition 100% full. At that point Linux wouldn't be able to boot any more as it needs to create some files on the drive while booting. Besides, the performance of Ext filesystems quickly degrade if the drive becomes too full so even while you can change the amount of reserved space or turn it off completely you probably don't really want to fill the drive to 100% full anyway...

---

