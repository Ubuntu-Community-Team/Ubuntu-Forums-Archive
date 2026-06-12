---
title: "Burned a DVD, but cant see the files on Win"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by bilbo.san on 2009-12-28
Hey everyone!
Hope anyone can help me... this is a little odd, I burned a DVD with some files for a client, I am able to reproduce the DVD and see the files on it, but when loading in on a Windows system, it wont see any files, it just says that the disc is empty... tried it on win xp and win 7.

Perhaps there is something with the settings... I read somewhere that something similar happened, but it was burned on win, worked on ubuntu but not on win...

Anyway... thanks for any comments.

e.

---

### Post by sandyd on 2009-12-28
burn with the propper filesystem.

in k3b, you can set the filesystem the cd is burned in.

---

### Post by bilbo.san on 2009-12-28
> **carlee said:**
> burn with the propper filesystem.

in k3b, you can set the filesystem the cd is burned in.

Thanks, I'll be checking that out... I guess it is better to use a USB memory.
:roll:

---

### Post by Mahngiel on 2009-12-28
windows doesn't like a filesystem that isn't ntfs or fat.  bear that in mind when you burn a disk and it's formatted with 'ext(3/4)'.  like carlee suggested, use k3b

---

### Post by falconindy on 2009-12-28
> **Mahngiel said:**
> windows doesn't like a filesystem that isn't ntfs or fat.  bear that in mind when you burn a disk and it's formatted with 'ext(3/4)'.  like carlee suggested, use k3b
Ext3/4 isn't a valid file system for a CD in **any** OS. Wikipedia claims:
> Microsoft Windows NT 4, Windows 2000, Windows XP, Windows Vista, Windows 7 can read ISO 9660 Level 1, 2, 3, Joliet, and ISO 9660:1999. Windows 7 may also mistake UDF format for CDFS. for more information see UDF.

---

### Post by Mahngiel on 2009-12-29
> **falconindy said:**
> Ext3/4 isn't a valid file system for a CD in **any** OS. 

that's EXT3 or EXT4. I don't know about you, but ubuntu is formatted as ext4 journaling on my hdd :confused:

---

### Post by lavinog on 2009-12-29
> **Mahngiel said:**
> that's EXT3 or EXT4. I don't know about you, but ubuntu is formatted as ext4 journaling on my hdd :confused:
They are discussing CD and DVD filesystems, for which EXT3 EXT4 NTFS and FAT are not valid.

---

