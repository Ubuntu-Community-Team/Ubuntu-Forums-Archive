---
title: "Mount partition to load at startup"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by mbwmex on 2008-12-29
Realize that this question has been posted/solved before but it seems that every post is different.

Info:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9059    72766386   83  Linux
/dev/sda2           37779       38913     9116887+   5  Extended
/dev/sda3            9060       22113   104856255   83  Linux
/dev/sda4           22114       24724    20972857+  83  Linux
/dev/sda5           37779       38913     9116856   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00063f74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS
mbw@mbw-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults                    0  0  
# /dev/sda1
UUID=a3b10949-65d3-46c1-88f1-3901c3b716b1  /                 ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=3b23ec1e-18a8-42ac-834f-169d26ad9700  none              swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda4                                  /media/MacDocs    ext3         defaults                    0  0  
/dev/sda5                                  /media/sda5       swap         defaults                    0  0  
/dev/sdb1                                  /media/MacBackup  ntfs         defaults                    0  0  

sda 3 Partion is not being recongized in "Places" also I want to mount it so it loads at startup. Name is "MacMedia".

Thanks for any help.

---

### Post by Dedoimedo on 2008-12-29
You do not have it listed in fstab.

Try first mounting it manually:

```

sudo mount -t ext3 /dev/sda3 /mnt

```

You can use any mount point instead of /mnt. Then use terminal or nautilus to navigate to the mount point.

When you see that it works, add the line to fstab. Backup first!!!

```

/dev/sda3 /media/MacMedia ext3 defaults 0 0 

```

Reboot or remount everything with mount -a. Make sure the MacMedia directory exists ...

Cheers,
Dedoimedo

---

### Post by jyaan on 2008-12-29
I would use the UUID instead of /dev/sda3. This is because with modern systems, it possible to change which drive is assigned to /dev/sda, /dev/sdb etc in the BIOS. With this way your drive will be identified regardless. You can find out the UUID of your drives with this command : ```
ls /dev/disk/by-uuid/ -l 
```

---

### Post by mbwmex on 2008-12-29
"MacMedia" is now listed again under "Media"  Ran the above command, got;
mbw@mbw-desktop:~$ ls /dev/disk/by-uuid/ -l
total 0
lrwxrwxrwx 1 root root 10 2008-12-29 12:41 03b053f2-ab28-4e68-822f-618cdfb6f91f -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-12-29 12:41 3b23ec1e-18a8-42ac-834f-169d26ad9700 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-12-29 12:41 6f739799-8189-49d2-9191-f81108c87797 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-12-29 12:41 79EC94766F7CDADB -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-12-29 12:41 a3b10949-65d3-46c1-88f1-3901c3b716b1 -> ../../sda1
So to auto mount sda 3 which is "MacMedia"  the command is: /dev/sda3 /media/MacMedia ext3 defaults 0 0

Seems like I am missing something?

Thanks for the help, greatly appreciated.
mbwmex

---

