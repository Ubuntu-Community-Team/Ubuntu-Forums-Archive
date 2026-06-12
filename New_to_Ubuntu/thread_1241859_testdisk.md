---
title: "testdisk"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by misterspiffy on 2009-08-16
Does anyone know how to 

restore a partition once you find it with testdisk?  Any help you be great

Below is w hat is listed after analyzing with testdisk:

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 300 GB / 279 GiB - CHS 36482 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1 35724 254 57  573922056
D HPFS - NTFS              0  32 33   191  89 26    3072000 [TOSHIBA SYSTEM VOLUME]
D HPFS - NTFS            191  89 27 36481  76 11  582998016 [SQ004576V03]










Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continueSegmentation fault
misterspiffy@misterspiffy-laptop:~$ 2 MB / 1500 MiB
misterspiffy@misterspiffy-laptop:~$ parted
WARNING: You are not superuser.  Watch out for permissions.
Warning: Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
GNU Parted 1.7.1
Using /dev/scd0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) 
(parted) sudo parted /dev/sda

---

### Post by LewRockwell on 2009-08-16
what the pros know...

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.forensicswiki.org/wiki/TestDisk](http://www.forensicswiki.org/wiki/TestDisk)

[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

(added link from post below)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

.

---

### Post by bumanie on 2009-08-16
This [page]("http://members.iinet.net.au/~herman546/p21.html") may also help you understand testdisk better.

---

