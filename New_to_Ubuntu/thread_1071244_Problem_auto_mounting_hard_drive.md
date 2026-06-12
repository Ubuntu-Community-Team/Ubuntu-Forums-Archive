---
title: "Problem auto mounting hard drive"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by djmac on 2009-02-16
I am having trouble auto mounting one of my hard drives. It will load manually (i.e. sudo mount /dev/sdc1 /media/Movies) - but is a real pain to do that every time (esp. seeing as a lot of people use the computer and others don't know how to do that). The other hard drive mounts fine (after using sudo pysdm)

There seems to be another partition or something in the problem drive too - can't figure out why (or how to get rid of it - reformatted it - twice)

sudo fdisk -l output:> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x200a88b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38158   306504103+  83  Linux
/dev/sda2           38159       38913     6064537+   5  Extended
/dev/sda5           38159       38913     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4420441f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS


/etc/fstab :> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                        0  0  
# /dev/sda1
UUID=0f0a1e8b-46c7-4884-849a-bbe718013322  /              ext3         relatime,errors=remount-ro                      0  1  
# /dev/sda5
UUID=4573a49e-93fa-4db5-8034-228102e8bc84  none           swap         sw                                              0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                           0  0  
/dev/sdb1                                  /media/TV      ntfs         nls=iso8859-1,users,umask=000                   0  0  
/dev/sdc2                                  /media/WinXP   ntfs         nls=iso8859-1,umask=000                         0  0  
/dev/sdc1                                  /media/Movies  ext3         owner,errors=remount-ro,group=dylan,users,user  0  0 

Cheers

---

### Post by cariboo on 2009-02-16
You are try to mount the drive as ext5 in fstab, while fdisk shows that /dev/sdc1 is an ntfs partition.

You should use something like this in fstab:

```
/dev/sdc1 /media/Movies **ntfs-3g** owner,errors=remount-ro,group=dylan,users,user 0 0 
```

Jim

---

### Post by djmac on 2009-02-16
Thanks mate worked a charm

---

