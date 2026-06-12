---
title: "Can't mount NTFS in 9.10"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by cartisdm on 2009-12-30
I can't mount the NTFS partition of my external harddrive now that I have a fresh install of 9.10.  I was working fine off this drive using a LiveCD of 8.10 and didn't have a problem.  I downloaded NTFS Configuration Manager and I'm still getting this error?

(see screenshot)

EDIT: I just noticed that I can access (read/write) the NTFS partition of my internal harddrive that I have Windows 7 installed on so Ubuntu must not like my external HDD for some reason.  Any ideas?

---

### Post by danastasio on 2009-12-30
try 
```
sudo apt-get install ntfsprogs
```

its possible that the install method that you used didn't install this for whatever reason.

---

### Post by oldfred on 2009-12-30
If you shut down abnormally  or if in windows it would want to run checkdisk then Ubuntu will not normally mount it. Some flag is set somewhere. There is a way to force mount it but if there is corruption you can damage that file(s). The checkdisk in windows will repair any damage or at least return the drive to mountable configuration.

---

### Post by cartisdm on 2009-12-30
> **danastasio said:**
> try 
```
sudo apt-get install ntfsprogs
```

its possible that the install method that you used didn't install this for whatever reason.

No luck with this method.

> If you shut down abnormally or if in windows it would want to run checkdisk then Ubuntu will not normally mount it. Some flag is set somewhere. There is a way to force mount it but if there is corruption you can damage that file(s). The checkdisk in windows will repair any damage or at least return the drive to mountable configuration.

I actually just ejected it out of a Mac computer (making sure to properly unmount it first).  How can I try forcing it to mount?

---

### Post by taurus on 2009-12-30
Use ntfsfix (part of the ntfsprogs package) to mount your ntfs partition.

---

### Post by cartisdm on 2009-12-30
> **taurus said:**
> Use ntfsfix (part of the ntfsprogs package) to mount your ntfs partition.

I tried it and still no luck.  Here are my results

```
daniel@daniel-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        7927    63562798    7  HPFS/NTFS
/dev/sda3            7928       14593    53544645    5  Extended
/dev/sda5            7928       14315    51311578+  83  Linux
/dev/sda6           14316       14593     2233003+  82  Linux swap / Solaris

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab8c8f26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       31262   251111983+   b  W95 FAT32
/dev/sdb2           31263       36484    41945683+   7  HPFS/NTFS
daniel@daniel-ubuntu:~$ sudo ntfsfix /dev/sdb2
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb2 was processed successfully.
daniel@daniel-ubuntu:~$ 

```

---

### Post by taurus on 2009-12-30
And have you tried to mount it by hand, from a terminal, again?

```
sudo /media/sdb2
sudo mount -t ntfs-3g /dev/sdb2 /media/sdb2
df -h
```

---

### Post by cartisdm on 2009-12-30
> **taurus said:**
> And have you tried to mount it by hand, from a terminal, again?

```
sudo /media/sdb2
sudo mount -t ntfs-3g /dev/sdb2 /media/sdb2
df -h
```

I didn't try it through the terminal.  Right now I am booting up my Windows XP cd and I'm gonna try to chkdsk the NTFS partition.  If that doesn't work I will try mounting it in a terminal in ubuntu

---

### Post by s3a on 2009-12-30
sudo apt-get install ntfs-3g

---

### Post by cartisdm on 2009-12-30
> **taurus said:**
> And have you tried to mount it by hand, from a terminal, again?

```
sudo /media/sdb2
sudo mount -t ntfs-3g /dev/sdb2 /media/sdb2
df -h
```

Same result

```
daniel@daniel-ubuntu:~$ sudo mkdir /media/sb2
daniel@daniel-ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb2 /media/sb2

Failed to read last sector (83891360): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
daniel@daniel-ubuntu:~$ 

```

---

### Post by cartisdm on 2009-12-30
Ok, I think I may have come up with what might be causing it.  I CAN NOT properly eject this external harddrive in Windows because it constantly tells me the device is in use (even right after booting up).  I am 99% certain this is due to my virus scanner either indexing the drive or scanning it or something, I'm not sure.  Since I am unable to properly eject the drive, Ubuntu isn't letting me mount it.

Any ideas on how I can force this eject or repair it in ubuntu?

---

### Post by taurus on 2009-12-30
Stop the antivirus from scanning that external drive.  Then, safely remove from windows before you unplug it.  

Otherwise, run the ntfsfix and mount it after that to see if that works.

---

### Post by cartisdm on 2009-12-30
Stopping the antivirus doesn't seem to be working but by using a 3rd party process scanner in windows it definitely shows AVG to be doing something with the external drive.

I tried doing an ntfsfix on the drive the trying to mount it in the terminal and STILL no luck.  I am going insane, all I want to do is mount this @$^#! drive....

```
**daniel@daniel-ubuntu:~$ sudo fdisk -l**

[sudo] password for daniel: 
[SIZE="2"]
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        7927    63562798    7  HPFS/NTFS
/dev/sda3            7928       14593    53544645    5  Extended
/dev/sda5            7928       14315    51311578+  83  Linux
/dev/sda6           14316       14593     2233003+  82  Linux swap / Solaris

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab8c8f26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       31262   251111983+   b  W95 FAT32
/dev/sdb2           31263       36484    41945683+   7  HPFS/NTFS
daniel@daniel-ubuntu:~$ sudo ntfsfix /dev/sdb2
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb2 was processed successfully.[/SIZE]

**daniel@daniel-ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb2 /media/sb2**
[COLOR="Red"]Failed to read last sector (83891360): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/COLOR]
```

---

### Post by oldfred on 2009-12-30
from:
[http://linux.die.net/man/8/mount.ntfs-3g](http://linux.die.net/man/8/mount.ntfs-3g)

options at the end of the mount command for ntfs
**force** Force the mounting even if the NTFS logfile is unclean. The logfile will be unconditionally cleared. Use this option with caution and for your own responsibility.

---

### Post by Mark Phelps on 2009-12-30
The general reason why we get external drive disconnect problems has to do with write buffering.  If you just shut off or remove an external drive while it is still being written to, that will most probably corrupt the filesystem on that drive because the file and directory entries aren't finalized until the writing is finished.

All that "safe removal" does is force the flushing of any write buffers, giving the drive time to finish before you remove it.

Thing is, though, if you go through a normal MS Windows shutdown, even with an external drive connected, that should accomplish the same thing.  Just turn off and disconnect your external drive after the PC is powered off and you should be OK the next time you go to connect the external drive.

---

