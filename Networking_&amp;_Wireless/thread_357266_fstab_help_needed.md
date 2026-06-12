---
title: "fstab help needed"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by Spaced Monkey on 2007-02-09
Hi,

I've got a strange situation.   I can start Ubuntu in x as root (well, I chose the emergency startup option from Grub and it seems to have root capability), and it's OK.   However, if I choose the normal Ubuntu startup from Grub, it halts at the 'hald' process.   

It was fine until I meddled with fstab:

here is my fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
//cowbeast/H2 /mnt/H2 smbfs username=blah,password=blah,dmask=777,fmask=777 0 0
//cowbeast/MEDIA /mnt/MEDIA smbfs username=blah,password=blah,dmask=777,fmask=777 0 0
//cowbeast/PHILHOMEDIRECTORY /mnt/PHILHOMEDIRECTORY smbfs username=blah,password=blah,dmask=777,fmask=777 0 0
``` 

Anything obviously wrong?

SpacedMonkey

---

