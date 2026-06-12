---
title: "Mounting Fat32 partition (shared data)"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Jay08 on 2010-11-22
I'm new to Linux Obviously...
i have Ubuntu dual booted with WinXP. HDD partitioned as:

/dev/sda1    NTFS         WinXP OS
/dev/sda2    FAT32        Shared Data
/dev/sda5    ext4           Ubuntu OS
/dev/sda4    swap

WinXP can read/write to sda2, however i cant seem to write to the disk in Ubuntu.

if i search it out i can play media from the partition, i just cannot find the location when saving .doc files, etc.

how do i mount the drive and make it r/w-able permanently?
    also i did look at the properties of the "drive" and it says the owner is "root"  idk if that affects anything...

thanks ahead of time, 
Jay

---

### Post by amjjawad on 2010-11-22
> **Jay08 said:**
> I'm new to Linux Obviously...
i have Ubuntu dual booted with WinXP. HDD partitioned as:

/dev/sda1    NTFS         WinXP OS
/dev/sda2    FAT32        Shared Data
/dev/sda5    ext4           Ubuntu OS
/dev/sda4    swap

WinXP can read/write to sda2, however i cant seem to write to the disk in Ubuntu.

if i search it out i can play media from the partition, i just cannot find the location when saving .doc files, etc.

how do i mount the drive and make it r/w-able permanently?
    also i did look at the properties of the "drive" and it says the owner is "root"  idk if that affects anything...

thanks ahead of time, 
Jay

Check [this]("http://ubuntuforums.org/showthread.php?t=872197") :)

---

### Post by Jay08 on 2010-11-22
thanks a ton, that's exactly what I needed.

---

### Post by amjjawad on 2010-11-23
> **Jay08 said:**
> thanks a ton, that's exactly what I needed.

Anything for a Linux user :)

Don't forget the mark this thread as SOLVED if you found what you were looking for :)

Good luck!

---

