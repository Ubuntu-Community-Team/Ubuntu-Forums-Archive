---
title: "only sdb and not sdb1"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by shankhs on 2010-12-19
Hi,
I was trying to create a bootable usb stick using dd_rescue , once dd_rescue completed its job then I tried to make the partition 1 bootable using :

```
sudo fdisk /dev/sdb
```

but I did something stupid after entering the above command and then 

```
tp
```

ofcourse the usb did not boot and then when I reentered ubuntu I got only /dev/sdb


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         374     2999296   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         374        6588    49912832   83  Linux
/dev/sda3            6588       24959   147568641    5  Extended
/dev/sda5            6588       24959   147568640   83  Linux

Disk /dev/sdb: 8036 MB, 8036285952 bytes
248 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15376 * 512 = 7872512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
```
Can somebody please tell me how to bring back /dev/sdb1 ? I dont have much of a knowledge about partitions but it seems that /dev/sdb1 is important.
Thank you

---

### Post by sikander3786 on 2010-12-19
Use Gparted or Disk Utility and create a new partition on sdb.

```
sudo apt-get install gparted
```

It would show under Applications > Accessories I think.

And Disk Utility is already installed under the System > Administration menu.

---

### Post by Joeb454 on 2010-12-19
Once Gparted is installed, that also appears under System>Administration.

The only time I've seen it under Applications>Accessories is on a Live CD

---

### Post by sikander3786 on 2010-12-19
> Once Gparted is installed, that also appears under System>Administration.

Right. Thanks for the correction :-)

---

### Post by shankhs on 2010-12-21
Thanks guys I will try and get back to you if there is still any prob.

---

