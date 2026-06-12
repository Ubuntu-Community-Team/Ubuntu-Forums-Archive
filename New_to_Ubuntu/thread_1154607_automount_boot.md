---
title: "automount boot"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Archer Troy on 2009-05-09
Hey guys,

I have 3 hard disks in my computer that im trying to automount to my /mnt on boot.  

heres fdisk -l
```
$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27929e80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460      182401  1453416615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584      182401  1452420553+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00080ddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121600   976751968+  83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007f14f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2      121601   976752000   83  Linux

```


im trying to mount all three into /mnt

so in fstab i have

```
/dev/sdb1 /mnt/sdb ext4 defaults 0 1
/dev/sdc1 /mnt/sdc ext4 defaults 0 1
```

and it mounts perfectly...but, id also like to mount my boot drive which is the sda drive. can someone explain to me how to mount it to /mnt/sda in fstab. 

thanks everyone.

---

### Post by blueridgedog on 2009-05-10
Your boot drive has many partitions.  Keep in mind you mount partitions and not drives.  Also your boot drive's partitions are likely to be mounted as your root file system, swap space and potentially another mount point.

/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460      182401  1453416615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584      182401  1452420553+  83  Linux

I would wager that that sda6 is mounted as your root file system.

To see what is mounted, use the command

```
mount
```

and post the output.  You can omit anything that isn't /dev/sda*.  I suspect they are already mounted.

---

