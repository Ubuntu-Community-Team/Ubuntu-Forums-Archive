---
title: "not able access the partitions"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by shrivatsa on 2010-11-14
i just  re installed Ubuntu ,formatted my disk ,now i am not able access the partitions or copy data to it.it says access denied somebody help please
:(

---

### Post by sikander3786 on 2010-11-14
Have you mounted those drives in fstab? You need to chown those drives.

```
sudo chown <username>:<username> /place/to/mount
```

If you can't figure that out, please post the output of these.

```
sudo fdisk -l
```

```
cat /etc/fstab
```

```
sudo blkid
```

---

### Post by shrivatsa on 2010-11-14
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcbf4d52e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9729    37190475    f  W95 Ext'd (LBA)
/dev/sda5            5100        9729    37190443+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003d9a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39061504   83  Linux
/dev/sdb2            4864       19458   117226497    5  Extended
/dev/sdb5            4864        9727    39061504   83  Linux
/dev/sdb6           14590       19458    39101440   83  Linux
/dev/sdb7            9727       14347    37108736   83  Linux
/dev/sdb8           14347       14589     1949696   82  Linux swap / Solaris



~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=3ea66e51-1c45-43a9-9887-52bf856dfbe2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
sagar@sagar-desktop:~$ sudo blkid
/dev/sda1: UUID="A2F01E63F01E3E4B" TYPE="ntfs" 
/dev/sda5: LABEL="usb 2" UUID="AAD41388D4135643" TYPE="ntfs" 
/dev/sdb1: UUID="3b9a401f-7b07-452f-92bc-7a8f279be9fb" TYPE="ext4" 
/dev/sdb5: UUID="59804c9f-c3dd-40b9-98d6-f264f876b1ba" TYPE="ext4" 
/dev/sdb6: UUID="bc5ea54a-f30f-45ac-85e1-adb3c1378feb" TYPE="ext4" 
/dev/sdb7: UUID="7e6449e0-8945-4477-b1a9-9930f5218976" TYPE="ext4" 
/dev/sdb8: UUID="3ea66e51-1c45-43a9-9887-52bf856dfbe2" TYPE="swap"


~$ sudo blkid
/dev/sda1: UUID="A2F01E63F01E3E4B" TYPE="ntfs" 
/dev/sda5: LABEL="usb 2" UUID="AAD41388D4135643" TYPE="ntfs" 
/dev/sdb1: UUID="3b9a401f-7b07-452f-92bc-7a8f279be9fb" TYPE="ext4" 
/dev/sdb5: UUID="59804c9f-c3dd-40b9-98d6-f264f876b1ba" TYPE="ext4" 
/dev/sdb6: UUID="bc5ea54a-f30f-45ac-85e1-adb3c1378feb" TYPE="ext4" 
/dev/sdb7: UUID="7e6449e0-8945-4477-b1a9-9930f5218976" TYPE="ext4" 
/dev/sdb8: UUID="3ea66e51-1c45-43a9-9887-52bf856dfbe2" TYPE="swap"

---

### Post by shrivatsa on 2010-11-14
> **sikander3786 said:**
> Have you mounted those drives in fstab? You need to chown those drives.

```
sudo chown <username>:<username> /place/to/mount
```

If you can't figure that out, please post the output of these.

```
sudo fdisk -l
```

```
cat /etc/fstab
```

```
sudo blkid
```

these is what i got for the first cmd

bash: sagar: No such file or directory

---

### Post by halitech on 2010-11-14
did you change <username> and /place/to/mount to the correct username and location?

---

### Post by shrivatsa on 2010-11-14
thanks sikander and halitech problem solved:):)

---

