---
title: "force option?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Clean1414 on 2008-12-27
i am helping a friend who accidentally loaded there pc with viruses, they want me to recover the data from there hard drive that has xp installed on it and then reinstall to that hard drive with ubuntu. this system uses IDE hard drives, i put in another ide hard drive in the pc to put the files on to, when i try to mount the hard drive with xp on it when in the live cd, it tells me that it can not mount the hard drive but if it has windows on it that i can use the force option. could someone tell me how to use the force option? the hard drive im trying to force to mount is the master on my IDE cable set up. thanks in advance

PS: im using the ubuntu 8.10 x64 live cd

---

### Post by sayems on 2008-12-27
PhotoRec is file data recovery software designed to recover lost files including video, documents and archives from Hard Disks and CDRom and lost pictures (thus, its 'Photo Recovery' name) from digital camera memory. PhotoRec ignores the filesystem and goes after the underlying data, so it will still work even if your media's filesystem has been severely damaged or re-formatted.

PhotoRec is free, this open source multi-platform application is distributed under GNU Public License. PhotoRec is a companion program to TestDisk, an app for recovering lost partitions on a wide variety of filesystems and making non-bootable disks bootable again. You can download them from this link.

For more safety, PhotoRec uses read-only access to handle the drive or memory support you are about to recover lost data from. Important: As soon as a pic or file is accidentally deleted, or you discover any missing, do NOT save any more pics or files to that memory device or hard disk drive; otherwise you may overwrite your lost data. This means that even using PhotoRec, you must not choose to write the recovered files to the same partition they were stored on


[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Clean1414 on 2008-12-27
> **sayems said:**
> PhotoRec is file data recovery software designed to recover lost files including video, documents and archives from Hard Disks and CDRom and lost pictures (thus, its 'Photo Recovery' name) from digital camera memory. PhotoRec ignores the filesystem and goes after the underlying data, so it will still work even if your media's filesystem has been severely damaged or re-formatted.

PhotoRec is free, this open source multi-platform application is distributed under GNU Public License. PhotoRec is a companion program to TestDisk, an app for recovering lost partitions on a wide variety of filesystems and making non-bootable disks bootable again. You can download them from this link.

For more safety, PhotoRec uses read-only access to handle the drive or memory support you are about to recover lost data from. Important: As soon as a pic or file is accidentally deleted, or you discover any missing, do NOT save any more pics or files to that memory device or hard disk drive; otherwise you may overwrite your lost data. This means that even using PhotoRec, you must not choose to write the recovered files to the same partition they were stored on


[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)


this is a realy good thing to know but i would like a faster alternative, my download speed and upload speed are not great so downloading a 700MB iso takes about 2 hours. is there a way i can recover within the ubuntu live cd?

---

### Post by bodhi.zazen on 2008-12-27
> **Clean1414 said:**
> this is a realy good thing to know but i would like a faster alternative, my download speed and upload speed are not great so downloading a 700MB iso takes about 2 hours. is there a way i can recover within the ubuntu live cd?

Yes

testdisk and photorec are both in the Ubuntu repostiories.

Boot the Ubuntu desktop CD, add the universe respositories, then apt-get install testdisk

There is a section on using this tool here :

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

