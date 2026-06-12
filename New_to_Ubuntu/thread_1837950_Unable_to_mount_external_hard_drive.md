---
title: "Unable to mount external hard drive"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by miryafa on 2011-09-02
I'm running Ubuntu 10.04, and the hard drive I'm using worked for awhile, but then I tried to put a bunch of things on it, left the computer alone for awhile, and when I came back I got the "unable to mount" error message again and again, no matter how much I restart.

I opened a terminal and I have the following I/O.  Any help is appreciated.

michael@michael-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf99b3d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29319   235504836   83  Linux
/dev/sda2           29320       30401     8691165    5  Extended
/dev/sda5           29320       30401     8691133+  82  Linux swap / Solaris

Disk /dev/sdd: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x28f12a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        7294    58589023+   7  HPFS/NTFS

michael@michael-laptop:~$ sudo df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             222G  7.7G  203G   4% /
none                  1.5G  296K  1.5G   1% /dev
none                  1.5G 1000K  1.5G   1% /dev/shm
none                  1.5G  192K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw

michael@michael-laptop:~$ sudo mount -t ntfs-3g /dev/sdd1 /media/external

$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdd1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by coffeecat on 2011-09-02
The answer is in the output to your mount command:

> **miryafa said:**
> NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware.

Since it worked before this you can exclude the fakeraid possibility, which leaves a hardware fault or filesystem inconsistency. Linux will not mount a damaged filesystem as a precaution against further damage. As NTFS is a Microsoft fileystem you need to run chkdsk from a Windows system to repair it. The Linux utility ntfsfix is not a viable alternative. You need a Windows system and chkdsk.

---

### Post by miryafa on 2011-09-02
Thanks for the tip Coffeecat.  I'll put that into play.

---

### Post by miryafa on 2011-09-05
And that worked!  I was able to use a friend's Windows XP and ran chkdsk /f on restart, restarted the computer, ran the chkdsk, restarted again, and then tried the hard drive with my linux, and it worked.

Thanks!

---

### Post by coffeecat on 2011-09-05
That's good news. I'm glad to hear it. :)

---

