---
title: "[SOLVED] How to run FSCK from LiveCD session I'm in now"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-01-01
I'm running my LiveCD session to run fsck against the drive I have a separate /home on. I want to run fsck against the partition that the ibex is in. 

I've opened a terminal and 

fsck

but no luck. Is there an easy way to do this? When I tried recovery mode, and fsck i got a message about 'serious damage'. What's up with that?

---

### Post by The Cog on 2009-01-01
Something like this maybe (check the device number - I guessed)?
> sudo fsck.ext3 /dev/sda6

---

### Post by drs305 on 2009-01-01
The Cog's suggestion will do the job as long as you have the correct partition designation.

> **Mark_in_Hollywood said:**
>  When I tried recovery mode, and fsck i got a message about 'serious damage'. What's up with that?

You shouldn't run fsck on a mounted partition, if that is what you were trying to do. Even in recovery mode, the system partition is mounted (although I think there was a plan for Intrepid to have fsck run when the recovery mode is selected). That is why you need to use the LiveCD to run a check on your system partition (or you can schedule an fsck check on the next boot from running system).

---

### Post by Mark_in_Hollywood on 2009-01-01
How do I determine the /dev?

I tried sudo ls -la in LiveCD and got butkus.

---

### Post by drs305 on 2009-01-01
> **Mark_in_Hollywood said:**
> How do I determine the /dev?

```
sudo fdisk -l
```
This will display all the partitions on your system. The root and /home partitions will be listed as *Linux* under the System column.

If you had your partitions labeled, you can see the labels with:
```

sudo blkid | grep "LABEL"

```

---

### Post by Mark_in_Hollywood on 2009-01-01
At some point in time, Linux/Ubuntu will have to somewhat standardize terminology.

Using Cog's

sudo fskc.ext3 /dev/sda1 

returned:

ubuntu@ubuntu:~$ sudo fsck.ext3 /dev/sda1
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Superblock invalid, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

and

ubuntu@ubuntu:~$ sudo e2fsck -b 8193 /dev/sda1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

So, why does it matter if it's ext2,3,4 or jfs. Why can't fsck work without so much user knowledge. Ouch!

---

### Post by The Cog on 2009-01-01
It is standardised. What makes you think otherwise?

I very much doubt that your /home partition is /dev/sda1. Can you post the content of the /etc/fstab from your running installation, and the output of the command **sudo blkid**?

---

### Post by Mark_in_Hollywood on 2009-01-01
Sorry, I don't know how to fix the problem I'm having. I say my /home is on  a sep. partition. It is /dev/sda5 and my OS (or whatever) is /dev/sda1. I need to know how and whether to check /sda1 AND/OR /sda5


I thought the output suggested the fsck couldn't read jfs file systems. My mistake. Thanks.

content of /etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f1af917f-002b-4c8a-8b30-82a687dea1f6 /               jfs     relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=993deece-4fba-477f-acd0-3b4f41b18b24 /home           ext3    relatime        0       2
# /dev/sda6
UUID=146ba48f-e433-437d-8095-6181223d87ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="f1af917f-002b-4c8a-8b30-82a687dea1f6" TYPE="jfs" 
/dev/sda5: UUID="993deece-4fba-477f-acd0-3b4f41b18b24" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="146ba48f-e433-437d-8095-6181223d87ae" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="UDISK 28X" UUID="0886-DD42" TYPE="vfat"

---

### Post by The Cog on 2009-01-01
I mis-read your original post and thought you wanted to fsck your /home partition. On re-reading, I see you want to fsck your / partition.

Your / partition is indeed /dev/sda1, but (unusually) it is jfs not ext3. So 
> sudo fsck.jfs /dev/sda1
should do the trick. Actually, this will also do it:
> sudo fsck /dev/sda1
I only just tried without specifying the filesystem type while writing this reply.

---

### Post by Mark_in_Hollywood on 2009-01-01
Results:

ubuntu@ubuntu:~$ sudo fsck /dev/sda1 
fsck 1.41.3 (12-Oct-2008)
fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 1/1/2009 23.45.26
Using default parameter: -p
The current device is:  /dev/sda1
Block size in bytes:  4096
Filesystem size in blocks:  2929846
**Phase 0 - Replay Journal Log
Filesystem is clean.

ubuntu@ubuntu:~$ sudo fsck.jfs /dev/sda1
fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 1/1/2009 23.45.44
Using default parameter: -p
The current device is:  /dev/sda1
Block size in bytes:  4096
Filesystem size in blocks:  2929846
**Phase 0 - Replay Journal Log
Filesystem is clean.

---

