---
title: "How to triple-boot Windows XP, Ubuntu 10.04 and Ubuntu 8.10?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by resander on 2010-05-04
I had Ubuntu 8.10 on my PC about a week ago, but corrupted it by requesting a package from an incompatible repository. With a lot of help from fellow Ubuntuers I managed to get a dual-boot with Windows XP and Ubuntu 10.04 up and working, but I just found out that the software I need to use is not yet available on Ubuntu 10.04. I can remove 10.04 and put an Ubuntu 8.10 back, but I would rather keep 10.04 and add Ubuntu 8.10 as a third OS.

Can that be done?

If so, I would shrink Ubuntu 10.04 a bit and put a small 8.10 into the freed space at the end of the Extended partition. But how do I define the mount points for Ubuntu 8.10. I have already used / for root partition and /home for home partition on Ubuntu 10.04. Do I need to specify two linux-swap partitions, one for each of 10.04 and 8.10? 

Anything else I need to do or know for a triple boot?

---

### Post by AXBX7C on 2010-05-04
Is running 8.10 virtually (Virtual Box) an option for you? You could boot into 10.04 or XP and run 8.10 in a box just when you need it for your programs... Of course, I don't recommend that if you use old hardware...

---

### Post by beloved88 on 2010-05-04
from what I know, that should be fairly straightforward. Just boot your live 8.10 cd/usb and install it as normal, and specify partitions manually.  the mount point for the partition for 8.10 whould not change from normal (just "/") since thats only the mount point for that os, not a global setting.  I don't know if there would be any grub/grub2 conflicts.  someone else have any ideas there?

---

### Post by ranch hand on 2010-05-04
The drive I am on right now is my test platform with several 10.04 installs, 8.04 and 9.10.

It is important to realize that there is a limit to the number of "primary" partitions to 4.  There is, however, extended partitons.

An extended partition is a type of primary partition that you can install an unlimited number of "logical" partitions in.  Gparted will do this for you.

You should run gparted from a Live CD so that you are not trying to partition a mounted drive.

---

### Post by garvinrick4 on 2010-05-04
> **resander said:**
> I had Ubuntu 8.10 on my PC about a week ago, but corrupted it by requesting a package from an incompatible repository. With a lot of help from fellow Ubuntuers I managed to get a dual-boot with Windows XP and Ubuntu 10.04 up and working, but I just found out that the software I need to use is not yet available on Ubuntu 10.04. I can remove 10.04 and put an Ubuntu 8.10 back, but I would rather keep 10.04 and add Ubuntu 8.10 as a third OS.

Can that be done?

If so, I would shrink Ubuntu 10.04 a bit and put a small 8.10 into the freed space at the end of the Extended partition. But how do I define the mount points for Ubuntu 8.10. I have already used / for root partition and /home for home partition on Ubuntu 10.04. Do I need to specify two linux-swap partitions, one for each of 10.04 and 8.10? 

Anything else I need to do or know for a triple boot? I have had a Windows, 9.04 and 10.04 and had no problems, gparted will make sure you have an extended so you can have all you got room for in linux. And you can resize or move in gparted all you want. I have done it just for the hell of it and gparted is good. The only thing I believe that will happen is the grub for 8.10 will overwrite if installed in sda. 
 You do not have a DELL with hidden recovery partition taking up sda1 do you?
Back to grub, there is no problem installing grub2 with Live CD if anything goofs up so no worrys at all really. Can you post the output of sudo fdisk -l and sudo blkid on thread just so I can see it, I am interested in where and if recovery resides and where grub2 is residing if hidden recovery. Would appreciate it.
 Also of course ubuntu live cd has gparted as stated in #4 but you can get an .iso of gparted from the website and burn a copy of just gparted, nice to have around really.

---

### Post by resander on 2010-05-05
Thanks for the encouraging comments!

The PC is a Compaq desktop with 2gb ram, 2.4GHz cpu and 150GB hard disk. 

Output from sudo FDISK -l

```

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x989a989a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19457   125572042    5  Extended
/dev/sda5            3825        5099    10241406   83  Linux
/dev/sda6            5100       18995   111619588+  83  Linux
/dev/sda7           18996       19457     3710983+  82  Linux swap / Solaris

Output by sudo BLKID

sudo blkid
/dev/sdb1: UUID="39fc0b07-4bbb-41d9-af6a-430f0160521d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="b9944c19-373d-496f-82bf-96a341579583" TYPE="swap" 
/dev/sda1: UUID="C4CC78CBCC78B96E" TYPE="ntfs" 
/dev/sda5: UUID="397edd98-014a-4f16-976a-429cea3cfbe9" TYPE="ext4" 
/dev/sda6: UUID="626a66b1-3287-461f-b51f-8f5a07ba7df4" TYPE="ext4" 
/dev/sda7: UUID="0b9b29f4-2f63-45eb-86c4-460ae4ac21c5" TYPE="swap"

```


And here is a transcription of the gparted display taken just now:
```

Partition   File system    Mount   Size[GB]   Used[GB] ... Flags
 /dev/sda1    nfts                  29.29      6.79        boot
 /dev/sda2    Extended             119.75
   /dev/sda5   ext4        /         9.77      2.47
   /dev/sda6   ext4        /home   106.45      2.17
   /dev/sda7   linux-swap            3.54

```

If I make the space for 10.04 a bit smaller it might look like this:

```

Partition   File system    Mount   Size[GB]   Used[GB] ... Flags
 /dev/sda1    nfts                  29.29      6.79        boot
 /dev/sda2    Extended             119.75
   /dev/sda5   ext4        /         9.77      2.47
   /dev/sda6   ext4        /home    86.45      2.17
   /dev/sda7   linux-swap            3.54
   /dev/sda8   ext4        /        20.00 

```


Q1.
I keep only one linux-swap partition since 10.04 and 8.10 are not running at the same time. Is that the right thing to do?

Q2.
I would shrink the 10.04 home partition to 86.25GB, move the linux-swap to be adjacent to it and make a 20GB parition at the end of the extended partition for a small version of 8.10 by gparted on the Live CD. I would not reinstall Ubuntu 10.04, only shrinking it by 20GB. I would then start installation from the Ubuntu 8.10 Live CD and select manual/advanced install and tick sda8 to be formatted and to have / as root partition. Is this the right way?

I have no knowledge about GRUB other than the stuff we put on our plates. Hope you can assist and dig me out if it goes wrong.

---

### Post by madjr on 2010-05-05
> **resander said:**
> Thanks for the encouraging comments!

The PC is a Compaq desktop with 2gb ram, 2.4GHz cpu and 150GB hard disk. 



Q1.
I keep only one linux-swap partition since 10.04 and 8.10 are not running at the same time. Is that the right thing to do?

Q2.
I would shrink the 10.04 home partition to 86.25GB, move the linux-swap to be adjacent to it and make a 20GB parition at the end of the extended partition for a small version of 8.10 by gparted on the Live CD. I would not reinstall Ubuntu 10.04, only shrinking it by 20GB. I would then start installation from the Ubuntu 8.10 Live CD and select manual/advanced install and tick sda8 to be formatted and to have / as root partition. Is this the right way?

I have no knowledge about GRUB other than the stuff we put on our plates. Hope you can assist and dig me out if it goes wrong.

q1: yep

you might find this useful (partitioning part)
[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)

---

