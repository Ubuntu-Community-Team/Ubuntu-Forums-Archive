---
title: "Mounting Problem"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by djmac on 2009-02-14
Hi all. I just reformated a hard drive (as ntfs) and I can't get it to mount. Apparently I don't have permission. The terminal said this after I tried to mount it manually:

wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What do I do?

Cheers

---

### Post by x33a on 2009-02-14
post the output of sudo fdisk -l

---

### Post by djmac on 2009-02-14
output of sudo fdisk -l :
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
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


---

### Post by x33a on 2009-02-14
the output seems ok.

did you try to mount it with sudo?

also, try it with ntfs-config.

and please post the output of /etc/fstab.

---

### Post by djmac on 2009-02-14
> dylan@dylan-desktop:~$ sudo mount /dev/sdc1 /media/Movies
[sudo] password for dylan: 
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

/etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                       0  0  
# /dev/sda1
UUID=0f0a1e8b-46c7-4884-849a-bbe718013322  /              ext3         relatime,errors=remount-ro     0  1  
# /dev/sda5
UUID=4573a49e-93fa-4db5-8034-228102e8bc84  none           swap         sw                             0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8          0  0  
/dev/sdb1                                  /media/TV      ntfs         nls=iso8859-1,users,umask=000  0  0  
/dev/sdc2                                  /media/WinXP   ntfs         nls=iso8859-1,umask=000        0  0  
/dev/sdc1                                  /media/Movies  ext3         errors=remount-ro,users        0  0  

 Don't know how to use ntfs config (don't have it I don't think)

---

### Post by x33a on 2009-02-14
hmm... the fstab output lists sdc1 as ext3.

open a terminal and type "sudo aptitude install ntfs-3g ntfs-config"

then use ntfs-config to mount the windows partition automatically.

in the meanwhile, open gparted and post the screenshots of all your hard drive partitioning. i assume you have 3 hard drives.

---

### Post by vanadium on 2009-02-14
You included sdc1 in /etc/fstab, but declared it as ext3. Either remove the line from /etc/fstab or, if you want the drive to automount, correct the line:

```

/dev/sdc1 /media/Movies ext3 errors=remount-ro,users 0 0 

```

should become

```

/dev/sdc1 /media/Movies ntfs nls=iso8859-1,umask=000 0 0 

```
(I also changed the options to be the same as your other ntfs volumes)

---

### Post by djmac on 2009-02-14
I just reformatted the whole disk again and started from scratch. Works fine now. Sorry if I wasted your time.

---

