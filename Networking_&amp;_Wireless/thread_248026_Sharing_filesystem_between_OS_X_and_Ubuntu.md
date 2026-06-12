---
title: "Sharing filesystem between OS X and Ubuntu"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by espenbe on 2006-08-31
In my local network at home, I have one Linux computer (Ubuntu Dapper) and two Apple-computers (OS X 10.4.7).  On one of the Apple-computers I have an external FW hard drive connected.  This disc is formatted as "Mac OS Extended Journaled".

How can I access the filesystems on this harddrive from my Linux-computer?


Espen

---

### Post by Uluen on 2006-08-31
```
man mount
```
> The  argument following the -t is used to indicate the file sys&#8208;              tem type.  The file system types which are  currently  supported              include:  adfs,  affs,  autofs,  coda, coherent, cramfs, devpts, efs, ext, ext2, ext3, hfs, hpfs,  iso9660,  jfs,  minix, msdos,cpfs,  nfs,  nfs4,  ntfs,  proc,  qnx4, ramfs, reiserfs, romfs,smbfs, sysv, tmpfs, udf, ufs, umsdos, usbfs, vfat,  xenix,  xfs, xiafs.Maybe you'll find your FS in there :)

---

### Post by espenbe on 2006-08-31
The harddrive is not connected directly to the Linux-computer.  I have to access it over the network.  If it was connected directly to the Linux-computer I would use HFS.

The question is in general "how can I mount a shared filesystem from an OS X-computer?"


Espen

---

### Post by Uluen on 2006-08-31
Can't you export the filesystem as NFS on the other Mac? I don't know much about Mac's but it shouldn't be hard as it's based on BSD?

---

### Post by skymt on 2006-08-31
Your options include [Samba](https://help.ubuntu.com/community/SettingUpSamba) and [SSHFS](http://fuse.sourceforge.net/sshfs.html), both in the repositories. NFS is also possible, but harder to set up.

---

