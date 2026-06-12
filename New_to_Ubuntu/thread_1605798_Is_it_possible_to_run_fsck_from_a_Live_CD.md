---
title: "Is it possible to run fsck from a Live CD?"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by diablo75 on 2010-10-25
I recently reinstalled Windows on a dual-boot setup and have been attempting to restore grub.  I have a separate thread started about that but have this one to ask a separate question that's related to it.

At the moment, I can't proceed per the instructions of the grub documentation (for restoring it) because the first step tells you to mount your / partition by selecting it from the places menu.  Except it's not showing up (but it does exist, according to fdisk).

So I was thinking that there might be some sort of error that's preventing it from being seen properly and was thinking I should focus on trying to fix that before grub.

For reference, here's the output from fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9697acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13944   112005148+   7  HPFS/NTFS
/dev/sda2           13945      121601   864754822    5  Extended
/dev/sda3           22455      120951   791177152+  83  Linux
/dev/sda5           13945       22454    68356543+  83  Linux
/dev/sda6          120952      121601     5221093+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x542be781

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS
ubuntu@ubuntu:~$
```

My root partition is sda5.

...

I just tried to run fsck against sda5, 3 and 2 (in that order).  I've not done this before exactly so I didn't know what to expect.  The output from 5 and 3 says "clean", but the output from 2 (the extended partition container) resulted in a "short read error":

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda5: clean, 158984/4276224 files, 1254272/17089135 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda3: clean, 66844/49455104 files, 50993889/197794288 blocks (check in 5 mounts)
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
ubuntu@ubuntu:~$ 

```

So, I'm not sure what to make of this...

---

### Post by trikster_x on 2010-10-25
Basically the output is telling you that your 2 linux partitions are fine.  Since sda2 is an extended partition, with sda3, 5, and 6 within it, fsck is unable to check it.  This is because an extended partition is basically a place holder that allows you to partition the drive further than the three or four main partitions allowed on a single HDD.

---

### Post by psusi on 2010-10-25
Yea, the extended partition contains other partitions, not a filesystem, so there's nothing there to check.

---

### Post by oldfred on 2010-10-25
It looks like sda3 is inside sda2, but you cannot have a primary inside the extended.

Besure to back up all your data as partition table errors can cause data loss. And fixing them incorrectly is often the biggest issue.

I would try testdisk to see if it will fixup partition table. 

There are command line ways to directly edit partition table if you are adventuresome.

Use fdisk to delete partition table & recreate - srs5694
[http://ubuntuforums.org/showthread.php?t=1597557&highlight=fdisk](http://ubuntuforums.org/showthread.php?t=1597557&highlight=fdisk)

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

Use sfdisk to edit partitions
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

---

### Post by psusi on 2010-10-26
Man, you're right... and this has to be the 10th person I've seen this week with a partition table corrupted in this way.  What broken program keeps doing this?

---

