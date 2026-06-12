---
title: "How can I mount/read an old SCO Unix SystemV Hard Disk with Ubuntu Linux?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by koenn on 2008-04-03
man mount 
> -t type

    Specify the filesystem type. Possible values include adfs, affs, autofs, coda, cramfs, devpts, efs, ext2, ext3, hfs, hpfs, iso9660, jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4, reiserfs, romfs, smbfs, sysv, tmpfs, udf, ufs, umsdos, vfat, xfs, and xiafs. The default type is iso9660. The type auto may also be used to set mount to autodetect the filesystem. When used with -a, this option can limit the types mounted. Use a comma-separated list to specify more than one type to mount. Prefix a list (or type) with no to exclude those types.

in stead of editing /etc/fstab, try a command syntax like this : 
```
mount -t xxx /dev/sda4 /mnt/medman
```
where xxx is a filesystem type. You can try them all. I'd start with  ' -t auto ' to see if mount can autodetect the filesystem type.

If all else fails, you can try to get data of the disk without mounting it. That works quite well for text. you can 'grep' or use the program  'strings' to find text on an unmounted partition, eg
[http://users.telenet.be/mydotcom/howto/data/recover.htm#undelete](http://users.telenet.be/mydotcom/howto/data/recover.htm#undelete)
[http://users.telenet.be/mydotcom/howto/data/recover.htm#strings](http://users.telenet.be/mydotcom/howto/data/recover.htm#strings)
This might get you the data you need, our you might find info (eg the SCO's fstab or whatever it's called on SCO) that tells you what file system was originally used.

---

