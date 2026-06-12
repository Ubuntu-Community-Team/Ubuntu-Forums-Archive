---
title: "Mounting Another External HD, when Ubuntu is already runing on another External HD"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by windy81 on 2009-07-09
how do i go about mounting another External Hard drive 
when im already running Ubuntu (latest desktop version) on a different External Hard Drive (dev/sdb)?

i've tried unplugging, and plugging it in, but to no avail :(

I have my music on there so it would be nice to get it connected up.

I'm totally new to ubuntu (installed 2 hours ago) so im rather used to things just connecting up in windows xp seamlessly.

Probably an easy solution for you pros out there :P

thanks

windy81

---

### Post by windy81 on 2009-07-09
**more info**

> dylan@dylan-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9403    75529566    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdac08953

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30027   241191846   83  Linux
/dev/sdb2           30028       30401     3004155    5  Extended
/dev/sdb5           30028       30401     3004123+  82  Linux swap / Solaris
[B]if that helps, this makes no sense to me. The external hard drive im trying to connect is a seagate Fat formatted HD

the 80GB disk is the internal HD (dev/sda), i dunno please help.
[/B]

---

### Post by windy81 on 2009-07-09
im trying , but google isnt helping me :(

---

### Post by Duffman3 on 2009-07-09
I'm pretty new to the ubuntu scene as well, but I would say your problem lies in the fact that the drive isn't mounted.

---

### Post by windy81 on 2009-07-09
on further inspection whilst trying to connect the other HD to the Ubuntu , its broke. The Hd wont even work with any computer now. and i've tried on sevaral other laptops...

same problem.... Usb device isnt recognised. malfunction error message comes up. 

so much for ubuntu... ******* pissed off. truly cos all my music is on there.

do you think that because the HD was connected, that the computer tried to boot up ubuntu from it and somehow broke the data integrity on it ?? 
so that when windows requests the identity of the said hard drive it now spitts out garble, instead of saying " seagate external hardrive" so that windows can configure the appropriate drivers ?

im at my wits end trying to ge it solved.

---

### Post by windy81 on 2009-07-09
please, i really need some help here.. i have no idea what to do.

---

