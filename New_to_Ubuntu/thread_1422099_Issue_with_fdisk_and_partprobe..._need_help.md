---
title: "Issue with fdisk and partprobe... need help"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by sazan on 2010-03-05
Hi

I have created a "non-root" user and that user just runs the script which in turn calls fdisk to create a partition.I have changed visudo to give the user permission to fdisk utility

Now, i create a new session with root and then do "partprobe", but i am encountering error when i try to create partition using "fdisk".

here is my fdisk output
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 33 265041 83 Linux
/dev/sda2 34 1077 8385930 83 Linux
/dev/sda3 1078 2121 8385930 83 Linux
/dev/sda4 2122 9729 61111260 5 Extended
/dev/sda5 2122 2382 2096451 82 Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System

```

and I am trying to create a partition on /dev/sda using my script.
Once the script is run, i start a session with root and do "partprobe" and then the above error comes.
Also, the partition is not created 


But, if i create partition by "root" on command line, the error is not seen and partition is created properly.

What seems to be the problem? Please help.

Thanks in advance

---

### Post by sazan on 2010-03-05
<bump> anyone?

---

