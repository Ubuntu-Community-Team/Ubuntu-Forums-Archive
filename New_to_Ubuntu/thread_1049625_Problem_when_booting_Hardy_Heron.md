---
title: "Problem when booting Hardy Heron"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by bosun1000 on 2009-01-24
I have a dual boot Ubuntu hardy heron and windows xp
when I boot up Ubuntu it always runs the routine check of drives but if I let it finish, the system just crashes before loading.The only way I can load Ubuntu is to press Esc to skip the drive check and then Ubuntu loads as normal.
Can you please help?
Thanks Bosun

---

### Post by taurus on 2009-01-24
Did you install hardy on it own partition and what is the filesystem that you used for hardy?  Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by bosun1000 on 2009-01-24
Hardy has it's own partition 
Not sure what you mean by "Filesystem" I am using Ver 8.04
Terminal outputs are:


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4c9d4c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       30401   141797722+   5  Extended
/dev/sda5           30214       30401     1510078+  82  Linux swap / Solaris
/dev/sda6           12749       30025   138777439+  83  Linux
/dev/sda7           30026       30213     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc671ad8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS
john@Home:~$ 





> **taurus said:**
> Did you install hardy on it own partition and what is the filesystem that you used for hardy?  Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

