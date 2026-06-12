---
title: "Windows+Ubuntu+Sabayon boot-loader question"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by ivanvajar on 2009-03-09
I just need a quick 'takealook'. I'm about to install Sabayon on another partition. Here is some output if needed.


ivan@ivan-desktop:~$ sudo fdisk -l
[sudo] password for ivan:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x076c076c

Device Boot Start End Blocks Id System
/dev/sda1 * 1 5083 40829166 7 HPFS/NTFS
/dev/sda2 5084 9964 39206632+ f W95 Ext'd (LBA)
/dev/sda5 5084 9964 39206601 7 HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3012f93

Device Boot Start End Blocks Id System
/dev/sdb1 * 18124 18247 996030 82 Linux swap / Solaris
/dev/sdb2 2 18123 145564965 f W95 Ext'd (LBA)
/dev/sdb3 18248 19457 9719325 7 HPFS/NTFS
/dev/sdb5 2 9670 77666211 7 HPFS/NTFS
/dev/sdb6 9671 14204 36419323+ 7 HPFS/NTFS
/dev/sdb7 14205 18123 31479336 83 Linux

Partition table entries are not in disk order

The idea is a clean install on one of the partitions of /dev/sdb. Both /dev/sda and /dev/sdb have GRUBs on them and Ubuntu is loaded from /dev/sdb. Do I need to take any precaution with this multi-boot regarding boot-loader options etc?

---

