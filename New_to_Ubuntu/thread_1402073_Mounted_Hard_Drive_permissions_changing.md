---
title: "Mounted Hard Drive permissions changing"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by parabol23 on 2010-02-08
I am having an issue when I choose to automatically mount my second hard drive in my system. When I mount using the disk utility program available through the software repositories I have no problem using it, I have read/write permissions on my main user account. When I opt to edit fstab to automatically mount the drive, it does automatically mount, but I lose all control over it and it can only be modified from root. 

Unfortunately I am not on the computer now and I cannot post the fstab contents but I know it has to be fixable from there. I was under the impression that using "user" in the options and "rw" will allow anyone to have read/write access, apparently I was wrong? I will post the fstab contents a little later. Thanks.

---

### Post by sisco311 on 2010-02-08
If it's an NTFS or FAT partition, then set the permissions & ownership in fstab:
```
UUID=<uuid here>    /mount/point    ntfs/vfat    defaults,dmask=0002,fmask=0113,gid=plugdev    0    2
```
[thread=283131]How to fstab[/thread]
[http://wiki.archlinux.org/index.php/NTFS_Write_Support#The_basic_ntfs-3g_options](http://wiki.archlinux.org/index.php/NTFS_Write_Support#The_basic_ntfs-3g_options)

---

