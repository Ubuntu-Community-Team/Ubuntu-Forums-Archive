---
title: "Nautilus crashes while opening a partition"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Viva on 2010-04-29
I was moving a large chunk of files to my external hard drive when my computer crashed. Since then, I can not open that particular partition on the external hdd using nautilus. I can still browse through the terminal and move the files. I need some help asap because there are some important files on that drive.

EDIT: I can open it using gksu nautilus

---

### Post by charliehorse55 on 2010-04-29
please run
```

sudo fdisk -l

```

And post the output back here.

---

### Post by Viva on 2010-04-29
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7a6b7a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   c  W95 FAT32 (LBA)
/dev/sda2            3649       13374    78124095    5  Extended
/dev/sda3           13983       19457    43977937+  83  Linux
/dev/sda4           13375       13982     4883760   82  Linux swap / Solaris
/dev/sda5            7296       13374    48829536   83  Linux
/dev/sda6            3649        7295    29294464+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dee51

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/sdb2            3825        7011    25599577+   f  W95 Ext'd (LBA)
/dev/sdb3            7012        9729    21832335    b  W95 FAT32
/dev/sdb5            3825        7011    25599546    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb9cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7454    59874223+   7  HPFS/NTFS
/dev/sdc2            7455       30401   184321777+  83  Linux

```

sdc is the hard drive I'm talking about and sdc2 is the partition. sdc1 is working fine.

---

