---
title: "USB mounting - Disk /dev/sdb doesn't contain a valid partition table"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by vasiauvi on 2010-04-10
Hello all,
I have an USB from work office and some important files on it. Some weeks ago it was enough just to put the USB stick in the USB port and automatically was mounted. 
I don't know what happened (strange things happens in Ubuntu some times) but now is just not automatically mounted. This was not a problem because I was mounting it manually!

Now, the same stick which in Windows is working great in my Ubuntu is impossible to mount even manually...

I've tried with a different USB stick and here is what it shows(I have 2 USB sticks in the 2 USB ports):
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8d32665

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19457   115330635    f  W95 Ext'd (LBA)
/dev/sda5            5100       11714    53126955    7  HPFS/NTFS
/dev/sda6           19307       19457     1212876   82  Linux swap / Solaris
/dev/sda7           16875       19306    19535008+  83  Linux
/dev/sda8           11714       16874    41455669+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 3906 MB, 3906994176 bytes
121 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7502 * 512 = 3841024 bytes
Disk identifier: 0x00000000

**Disk /dev/sdb doesn't contain a valid partition table**

Disk /dev/sdc: 2015 MB, 2015363072 bytes
17 heads, 16 sectors/track, 14471 cylinders
Units = cylinders of 272 * 512 = 139264 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14472     1968001+   6  FAT16

```

Can anyone tell me what I have to do to make the office USB stick to work on my system?

Thanks!

---

### Post by srs5694 on 2010-04-10
First, which disk is it that's the problem one, /dev/sdb or /dev/sdc? Both are smallish (~4GB and ~2GB, respectively), and so could be the USB flash drive you describe.

Second, what command, *precisely*, were you using to mount the disk? Most importantly, were you referencing the disk as a whole (/dev/sdb or /dev/sdc) or a partition on it (such as /dev/sdb1 or /dev/sdc1)?

---

### Post by ibuclaw on 2010-04-10
> **vasiauvi said:**
> Hello all,
I have an USB from work office and some important files on it. Some weeks ago it was enough just to put the USB stick in the USB port and automatically was mounted. 
I don't know what happened (strange things happens in Ubuntu some times) but now is just not automatically mounted. This was not a problem because I was mounting it manually!

Now, the same stick which in Windows is working great in my Ubuntu is impossible to mount even manually...


If you have data kept on it, backup all files/folders the device, then reformat the USB stick with the defective partition table. Finally restoring any data that you took off it.

Regards
Iain

---

### Post by vasiauvi on 2010-04-11
> **srs5694 said:**
> First, which disk is it that's the problem one, /dev/sdb or /dev/sdc? Both are smallish (~4GB and ~2GB, respectively), and so could be the USB flash drive you describe.

Second, what command, *precisely*, were you using to mount the disk? Most importantly, were you referencing the disk as a whole (/dev/sdb or /dev/sdc) or a partition on it (such as /dev/sdb1 or /dev/sdc1)?

Hello,
Thanks for replying!
First I want to correct what I've said in the first post, and have to say that the USB stick of 4GB is also not working in Windows. It's saying that is not formatted! 

The disk with problem is /dev/sdb ~4GB.
Mounting the disk I've used this:
```
sudo mount /dev/sdb /mnt/usbstick/
mount: you must specify the filesystem type

```

When trying 
```
vasia@vasia-laptop:~$ sudo mount /dev/sdb1 /mnt/usbstick/
mount: special device /dev/sdb1 does not exist

```
> 
If you have data kept on it, backup all files/folders the device, then reformat the USB stick with the defective partition table. Finally restoring any data that you took off it.

How to do that?
I've tried this tutorial from [Linuxjournal.com]("http://www.linuxjournal.com/article/8366?page=0,0") but i was lost and stoped :(

I've downloaded some programs in Windows and recovered the data from the stick but the file that I needed most is not opening. Tomorrow I have to take the stick back to the office and ...well, I have to format it!

---

### Post by topviet on 2011-02-27
> **vasiauvi said:**
> Hello all,
I have an USB from work office and some important files on it. Some weeks ago it was enough just to put the USB stick in the USB port and automatically was mounted. 
I don't know what happened (strange things happens in Ubuntu some times) but now is just not automatically mounted. This was not a problem because I was mounting it manually!

Now, the same stick which in Windows is working great in my Ubuntu is impossible to mount even manually...

I've tried with a different USB stick and here is what it shows(I have 2 USB sticks in the 2 USB ports):
```

**Disk /dev/sdb doesn't contain a valid partition table**

```
Can anyone tell me what I have to do to make the office USB stick to work on my system?

Thanks!

I have same problem. I bought a 16GB HP v125w USB drive a week ago. Put some files on the USB drive. Used it everyday until yesterday. For some reasons, it's not auto mount.  I checked the Disk Utility. It recognized the USB drive HP v125w.

Manual mount the drive, did not work. Yes, I guess I can reformat the drive to use. But, I just wonder there is a way to recover or read my files from that USB drive.

Any ideas? Thanks.

---

