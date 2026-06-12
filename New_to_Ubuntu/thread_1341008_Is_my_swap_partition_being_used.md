---
title: "Is my swap partition being used?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Bakudan00 on 2009-11-29
Okay, I made a 5GB linux-swap partition when I was dividing my drive up for a Win7/Karmic dual-boot. Thinking that Ubuntu would detect and use it automatically, I didn't set a mount point to it during installation like I did pointing / and /home to separate partitions. My question is whether or not that partition is being used (I suspect it isn't), and if it isn't how do I achieve that without installing again?

I followed some info from the [swap faq]("https://help.ubuntu.com/community/SwapFaq#Should%20I%20reinstall%20with%20more%20swap?") and got this:
```

eric-admin@eric-admin-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfb5dfb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530        1543      102400    7  HPFS/NTFS
/dev/sda3            1543        7280    46080000+   7  HPFS/NTFS
/dev/sda4            7281       38913   254092072+   5  Extended
/dev/sda5            7281       10467    25599546   83  Linux
/dev/sda6           11742       12378     5116671   82  Linux swap / Solaris
/dev/sda7           12379       38913   213141164+   7  HPFS/NTFS
/dev/sda8           10468       11741    10233373+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0868ace

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS
eric-admin@eric-admin-laptop:~$ sudo swapoff -a
eric-admin@eric-admin-laptop:~$ sudo /sbin/mkswap /dev/sda6
Setting up swapspace version 1, size = 5116664 KiB
no label, UUID=e4536d40-25c8-4841-806b-cf47064cc58d
eric-admin@eric-admin-laptop:~$ sudo swapon -a
swapon: cannot find the device for UUID=526ad403-38e0-45f8-9452-72cb63cd93a9
eric-admin@eric-admin-laptop:~$ 

```What does that mean, "cannot find device?"

Many thanks in advance.

---

### Post by cjohnston on 2009-11-29
If you run 'free -m' the last line will tell you about your swap usage. Swap gets used when you run out of RAM.

---

### Post by Bakudan00 on 2009-11-29
This is what free -m gives me:

```

eric-admin@eric-admin-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3708       3595        113          0       1530       1359
-/+ buffers/cache:        705       3002
Swap:            0          0          0
eric-admin@eric-admin-laptop:~$ ^C
eric-admin@eric-admin-laptop:~$ 

```And I was copying over 7 GB of music from an external drive when I ran that. Does a value of 0 for my swap total mean what it sounds like? That I have no swap?

---

### Post by gdonwallace on 2009-11-29
By the way that output looks, You may not have an active swap partition.  However; I would run the disk utility under administration.  This will show all partitions that are setup in Ubuntu.  

As swap is a virtual partition, it will not show up as a mounted partition on your system.  The Disk Utility will show what and how your disk has been partitioned, including swap.  If there is no swap setup, you can also use disk utility to setup the swap.

---

### Post by wojox on 2009-11-29
You probably need to change the uuid in fstab. Have a look here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Bakudan00 on 2009-11-29
Disk Utility says I have a 5.2 GB swap space, dev/sda6, like fdisk showed earlier. It also says it's not mounted. Is there a way to fix this through the disk utility without modifying the fstab like wojox suggested, or am I going to have to get my hands dirty? Forgive me, I'm a linux newbie going on 5 days experience. Thus, I have no clue what the hell I'm doing. ;)

Edit: Assuming after some more investigation I will have to get my hands dirty, what do I change the uuid to?

---

### Post by Bakudan00 on 2009-11-29
Ah ha!

I found [this thread]("http://ubuntuforums.org/showthread.php?t=1338175") and was able to fix it. Thanks everyone for putting up with my newb-ness. :D

---

### Post by gdonwallace on 2009-12-21
Something I just noticed on your out put was that swap (/dev/sda6) is listed as swap / Solaris.  

Are you running a dual boot with Solaris also installed?  If so, this will cause problems.  The "partition code" that Linux uses to identify a partion as swap and the "partition code" that Solaris uses to identify a partion as usable disk space (i.e. space to store files) is the same thing.  In effect anything that gets saved to that partition from Solaris will get deleted/corrupted by Linux (ubuntu or otherwise)  Or could cause some other really nasty problems with the way linux views that partition.

If you are running a dual boot w/ Solaris, I would highly suggest that you do not do that, to save your self some really nasty headaches.

---

