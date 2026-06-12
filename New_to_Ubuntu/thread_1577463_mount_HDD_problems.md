---
title: "mount HDD problems"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by k33bz on 2010-09-18
So I decided to start a FileServer, all has gone well except adding an extra HDD. I had already formatted to an ext3 before I installed it in my server.

```
root@server1:/media/store# mount /dev/sdb1 /media/store
mount: you must specify the filesystem type

```

So I added the -t

```
root@server1:/media/store# mount -t ext3 /dev/sdb1 /media/store
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I tried also as ext2, and get the same thing.

```
root@server1:/media/store# dmesg | tail 
[ 2112.285584] attempt to access beyond end of device
[ 2112.285591] sdb1: rw=0, want=4, limit=2
[ 2112.285597] EXT3-fs: unable to read superblock
[ 2285.980448] attempt to access beyond end of device
[ 2285.980455] sdb1: rw=0, want=4, limit=2
[ 2285.980460] EXT2-fs: unable to read superblock
[ 3301.170991] VFS: Can't find ext3 filesystem on dev sdb.
[ 3312.221371] attempt to access beyond end of device
[ 3312.221378] sdb1: rw=0, want=4, limit=2
[ 3312.221384] EXT3-fs: unable to read superblock

```

Also tried this 

```
root@server1:/media/store# /dev/sdb1  /media/store  ext3  defaults  0  1
bash: /dev/sdb1: Permission denied

```

and as you see I am running as root so I do not understand why I am getting denied. (and no I dont want to hear that it is a bad idea to run as root) 

```
root@server1:/media/store# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030caa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       38914   312320001    5  Extended
/dev/sda5              32       38914   312320000   8e  Linux LVM

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0c4b2ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081    5  Extended

```

Also FYI I am running my server through ssh, no monitor or keyboard attached to the server itself.

---

### Post by formaldehyde_spoon on 2010-09-18
The disk is actually formatted as ext2, yes?  
It isn't formatted as both ext2 AND ext3 so I'm not surprised you get at least one "bad superblock". ;)

You're getting permission denied because you forgot "mount"

---

### Post by garyed on 2010-09-18
Your fdisk shows an extended partition for sdb1 but no linux file system.
You would get the same results if you tried to mount sda2.
I dont quite understand how extended partitioning works but I don't think its complete for sdb drive.

---

### Post by k33bz on 2010-09-18
> **garyed said:**
> Your fdisk shows an extended partition for sdb1 but no linux file system.
You would get the same results if you tried to mount sda2.
I dont quite understand how extended partitioning works but I don't think its complete for sdb drive.

Ok, so what do I need to do to that HDD (sdb) before I can add its hdd space to my file server?

---

### Post by garyed on 2010-09-18
> **k33bz said:**
> Ok, so what do I need to do to that HDD (sdb) before I can add its hdd space to my file server?

I would just be guessing so you might want to wait for some better answers.
Assuming there's no data on the drive yet you could delete & repartition with gparted & make sure to use ext3 file system.
Good luck

---

### Post by k33bz on 2010-09-18
> **garyed said:**
> I would just be guessing so you might want to wait for some better answers.
Assuming there's no data on the drive yet you could delete & repartition with gparted & make sure to use ext3 file system.
Good luck

Naw, on that 40gigger there is no information at all on it. I had to transfer info from that HDD from a previous desktop installation, then I reformatted it (via USB cable). So I decided to couple it inside my server as extra space, just cant seem to mount it. So maybe after I am through with my file transfer (roughly another 28 hours) I will reformat it again, but this time inside my server.

Unless I find a different route to go by by the time I am done with file transfers.

---

### Post by formaldehyde_spoon on 2010-09-19
There is no other route.
Apologies if I was less than clear above: you can't mount a partition as ext2 (or ext3 ) unless it IS actually an ext2 partition (or ext3, as the case may be).
Your sdb1 partition has not been formatted as ext2, hence you can't mount it as ext2.

---

### Post by k33bz on 2010-09-19
> **formaldehyde_spoon said:**
> There is no other route.
Apologies if I was less than clear above: you can't mount a partition as ext2 (or ext3 ) unless it IS actually an ext2 partition (or ext3, as the case may be).
Your sdb1 partition has not been formatted as ext2, hence you can't mount it as ext2.

ya but what do I mount it as, I mean that is what I formatted it at (ext3)

---

### Post by QLee on 2010-09-19
[QUOTE=k33bz]ya but what do I mount it as, I mean that is what I formatted it at (ext3)[/QUOTE]
From the data that you have shown us so far, you created an extended partition (which is meant to be a container for logical volumes), but you did not create any logical partitions within it. You should be formatting and mounting sdb5 if you are going to use an extended partition.

---

### Post by Lateralis on 2010-09-19
You cannot mount that partition on sdb as it stands because it is an extended partition.  

This is a partial fdisk output for the hard drive my Ubuntu is on:

```

/dev/sdb3           12179       19452    58428405    5  Extended
/dev/sdb5           12179       12300      979933+  82  Linux swap / Solaris
/dev/sdb6           12301       19452    57448408+  83  Linux

```

The extended partition contains sdb5 and sdb6 as logical partitions.  I cannot mount sdb3 - it doesn't make sense to do so - but the other two do mount; it is how I am in Ubuntu! 

So, I think you can either create a new logical partition within that extended one and mount that logical partition, or just write a primary partition that isn't Extended.

---

