---
title: "Grub 2 Problem - Multiple hard disks"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by jestinjoy on 2010-04-14
I have 2 hard disks. In the first Windows is installed. In the second(Slave), Ubuntu Karmic is installed. My problem is that Grub is taking bit longer to load. What may be problem. Please help. Whether its the new grub problem or having 2 hard disks?

HAve Ubuntu installed in sdb6:guitar:

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         765     6144831    7  HPFS/NTFS
/dev/sda2             766        9728    71995297+   f  W95 Ext'd (LBA)
/dev/sda5             766        3315    20482843+   7  HPFS/NTFS
/dev/sda6            3316        5865    20482843+   7  HPFS/NTFS
/dev/sda7            5866        7777    15358108+   7  HPFS/NTFS
/dev/sda8            7778        9728    15671376   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01ad01ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3187    25599546    7  HPFS/NTFS
/dev/sdb2            3188        9729    52548615    f  W95 Ext'd (LBA)
/dev/sdb5            3188        6374    25599546    7  HPFS/NTFS
/dev/sdb6            8414        9729    10570738+  83  Linux
/dev/sdb7            6375        6496      979933+  82  Linux swap / Solaris
/dev/sdb8            6497        8413    15398271   83  Linux
```

---

### Post by oldfred on 2010-04-15
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

alternate - grub1.98 will be in Lucid
Very long boot solved with experimental grub1.98 post8
[http://ubuntuforums.org/showthread.php?t=1367488](http://ubuntuforums.org/showthread.php?t=1367488)

reinstall from working system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub

---

