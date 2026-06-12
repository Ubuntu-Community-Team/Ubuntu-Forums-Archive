---
title: "Can not mount volume (DVD)"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by lobbert on 2009-06-29
**Help! Can not mount volume (DVD)**             
                                                                [SIZE=2]Hi, my ubuntu system is  8.04..2.
When I tried to install the LabVIEW on my computer, (I try to use DVD to install.) it said "Cannot mount volume. invalid mount option when attempting to mount the volume 'ASLSP09MacLinux'."[/SIZE]:confused:
[SIZE=2]
My result for "sudo fdisk -l" is[/SIZE]

[SIZE=2]Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94dfead2
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2            9143       24321   121925317+  83  Linux
/dev/sda3            8535        9142     4883760   82  Linux swap / Solaris
/dev/sda4              25        8534    68356575   83  Linux
Partition table entries are not in disk order
Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024d7b
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux[/SIZE]

[SIZE=2]The result for "sudo cat /etc/fstab" is[/SIZE]

[SIZE=2]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ba5bd5a0-a5db-4b4c-8075-35f9a14163c7 /               xfs     relatime        0       1
# /dev/sda1
UUID=8bfe7efd-b0b4-47ef-ba75-dda7887f5bad /boot           ext2    relatime        0       2
# /dev/sdb1
UUID=a647a451-7692-41e8-9bd3-84e956ec9e67 /home           xfs     relatime        0       2
# /dev/sda4
UUID=d0cf0d29-374b-4e02-827b-1740719b985c /user           xfs     relatime        0       2
# /dev/sda3
UUID=2686784f-4301-4b5c-b235-db980204d1d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[/SIZE] 
Could you give me some suggestion?
It seems that my DVD rm can read out other disks except this one(LabVIEW). But this disk should be OK because another computer with SUSE system can read it.

Thanks a lot.
                                                                                                                                                 
                                        
                                                                                                                                                                     lobbert                   [View Public Profile]("http://ubuntuforums.org/member.php?u=861700")                   [Send a private message to lobbert]("http://ubuntuforums.org/private.php?do=newpm&u=861700")                             [Find More Posts by lobbert]("http://ubuntuforums.org/search.php?do=finduser&u=861700")

---

### Post by LewRockwell on 2009-06-29
fstab shows cdroms and no dvdroms

has it worked with other DVDs before?

---

### Post by lobbert on 2009-06-30
It seems it can read another DVD.

---

