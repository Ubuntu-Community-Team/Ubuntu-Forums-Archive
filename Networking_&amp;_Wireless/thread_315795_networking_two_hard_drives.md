---
title: "networking two hard drives"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by STREETURCHINE on 2006-12-09
I am trying to work out how to get hdb1 (edgy)to see hda1(dapper) ,
from hda1 i can browse hdb1 ,but i dont seem to be able to configure it so hdb1 sees hda1,any idea's  :D

---

### Post by adaptr on 2006-12-09
If both of these drives are in the same machine, then "networking" is completely the wrong term to use.

How you get one to see the other - exactly the same way as you did with the reverse situation, of course.
Since you don't tell us what you did before, it's rather hard to tell you how to do it this time.

---

### Post by FrodoB on 2006-12-09
Publish the outputs of the two different copies of /etc/fstab for both Dapper and Edgy and we can tell you how to modify them to make this work in both cases.

---

### Post by STREETURCHINE on 2006-12-09
yes the hard drives are on the same box, but i never installed the second harddrive it was done at computer shop and the tech set it up as a slave to hda1 with dapper on both hard drives, i decided to give edgy a go and loaded it on to hdb1 so there for i cant help with how he mounted hda1 to hdb1.

 so i was just trying to find out how it is done.

---

### Post by FrodoB on 2006-12-09
You just need the proper entry in /etc/fstab to mount the other drive onto a directory like /media/hda1 or /media/hdb1

---

### Post by STREETURCHINE on 2006-12-09
> **FrodoB said:**
> Publish the outputs of the two different copies of /etc/fstab for both Dapper and Edgy and we can tell you how to modify them to make this work in both cases.


this may sound stupid but what command do i type in to get the /etc/fstab out put ,i tried /etc/fstab =permission denied.so i tried sudo /etc/fstab  =no such file or directory.

---

### Post by FrodoB on 2006-12-09
If is owned by root so in a terminal window type:

sudo gedit /etc/fstab

should get you in with read/write access.

---

### Post by STREETURCHINE on 2006-12-09
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext2    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb1     ext3    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
 
that is hda1,have to reboot to get the outher one

---

### Post by STREETURCHINE on 2006-12-09
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=341c2a1e-fbdb-4332-a4a2-269783187beb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=b0c324a2-f2d1-424e-b97f-e4fc83fe72d9 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

that is for hdb1

---

### Post by FrodoB on 2006-12-09
OK we really need to see the /etc/fstab from the other Ubuntu to have the whole story here.

---

### Post by adaptr on 2006-12-10
> **STREETURCHINE said:**
> /etc/fstab: static file system information.
/dev/hda1       /               ext2    defaults,errors=remount-ro 0       1

That's it.
Just change the / to /media/hda1 and you're done:

> /dev/hda1 /media/hda1 ext2 defaults,errors=remount-ro 0 1

---

