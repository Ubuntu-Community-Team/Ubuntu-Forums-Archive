---
title: "wht is this extended partition intended for?"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Franz01 on 2010-05-17
I do not understand why I have the extended partition here below:

```

root@xxxxxx:~# fdisk -l

Disk /dev/sda: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device    Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4238    34041703+  83  Linux
**/dev/sda2            4239        4425     1502077+   5  Extended**
/dev/sda5            4239        4425     1502046   82  Linux swap / Solaris
```

Only the sda1 is mounted

```

root@xxxxxx:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             33506948   6856504  24948360  22% /
varrun                  257688        92    257596   1% /var/run
varlock                 257688         0    257688   0% /var/lock
procbususb              257688    257676        12 100% /proc/bus/usb
udev                    257688    257676        12 100% /dev
devshm                  257688         0    257688   0% /dev/shm 
```

Does it mean that the system was intended to use more partitions, but now the extended one is useless?

thank you

---

### Post by tom.swartz07 on 2010-05-17
in a sense.

Many times, users format separate partitions for their data, for example they would have a /home partition so that their information is backed up between installs.
Other people have other operating systems installed.

There is a limit on how many primary partitions- 4 I believe..
By making an extended partition, you could get around this- one extended could have as many partitions as you want on it!

Just as a reference, Here's what mine looks like: I have a few extra backup partitions:

```
tom@tardis:~$ sudo fdisk -l
[sudo] password for tom: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e5b244a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3983    31993416   83  Linux
/dev/sda2            3985       38913   280567162    5  Extended
/dev/sda5           38428       38913     3903763+  82  Linux swap / Solaris
/dev/sda6            3985        7631    29294496   83  Linux
/dev/sda7            7632       31568   192273921    7  HPFS/NTFS
/dev/sda8           31569       38427    55094886   83  Linux

Partition table entries are not in disk order

```

---

