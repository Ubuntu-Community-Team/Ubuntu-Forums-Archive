---
title: "partition mounting problem"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by Garthhh on 2010-05-12
I allocated 40g partition [sda1] for a future dualboot, I'm guessing that because I can't resize sda6 & it has 4g of something on it that it's the active partition
I have the 10.04 iso on my active partition [desktop]
I can't mount sda1, when I run
sudo fdisk -l
df -h I notice that the mount point is *

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026a8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4557    36604071   83  Linux
/dev/sda2            4558       19458   119685915    5  Extended
/dev/sda5           19275       19458     1466368   82  Linux swap / Solaris
/dev/sda6            4558       19090   116736291   83  Linux
/dev/sda7           19091       19274     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8036 MB, 8036285952 bytes
248 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15376 * 512 = 7872512 bytes
Disk identifier: 0x000bfb92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1

I found [this]("https://help.ubuntu.com/community/Installation/FromLinux") which should let me do an install without having to use any outside media

---

### Post by cariboo on 2010-05-12
The ***** just denotes that the partition is bootable, fdisk only shows your partitions, not where the are mounted.

The reason you may not be able to mount /dev/sda1 is that it is already mount. I always use:

```
df -h
```

or

```
mount
```

to see which partitions are mount where. The mount command gives me more information then I really need so I mostly use the df command.

---

### Post by Garthhh on 2010-05-12
I'm running 8.04 & trying to get to 10.04 & haven't had good success [black screen after splash with progress bar under], doing the install on my pc then putting the HDD back in my gateway 7330gz, that has no working CD & won't boot from USB [no bios support]

when I go to places & click on it nothing
When I right click mount is one of the choices [nothing happens]
which wouldn't be there if it were already mounted, I thought?

I copy the 10.04 iso open a file browser, right click on an icon of a HDD labeled 37.5 GB media, [no paste option] which is the same size indicated on Gparted 

here is  the out put when I put the code you gave me in terminal

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             111G  3.5G  102G   4% /
varrun                744M  100K  744M   1% /var/run
varlock               744M     0  744M   0% /var/lock
udev                  744M   52K  744M   1% /dev
devshm                744M   52K  744M   1% /dev/shm
lrm                   744M   40M  705M   6% /lib/modules/2.6.24-27-generic/volatile
gvfs-fuse-daemon      111G  3.5G  102G   4% /home/garthh/.gvfs
/dev/sdb1             7.5G  827M  6.7G  11% /media/disk

---

