---
title: "Problems with installing on a flash drive"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by wizkid250 on 2009-08-14
I installed Ubuntu on my flash drive, and now, unless i have it plugged in when it starts up, I cannot start up into Windows XP
how can this be fixed?

---

### Post by berthiggins on 2009-08-14
you have modified the bootloader on your hard disk .
You need to do 2 things 
1. boot your windows XP with the CD select recovery and type fixmbr
this will put your hard disk back where it was before.
2 you now need to fix the ubuntu install on your flash drive if it is a new install then it would probably be easier to reinstall ( you could fix it if you want the practice)
When you reinstall click advanced at the end of the install and select your flash drive as the place to install grub rather than your hard disk.

---

### Post by wizkid250 on 2009-08-14
i do not have any of the windows disks-is there an alternative method?

---

### Post by LewRockwell on 2009-08-14
> **wizkid250 said:**
> i do not have any of the windows disks-is there an alternative method?

create a small partition on your main drive, place the menu.lst file there and then point your MBR to that

(note: we could explain this process but there are already tutorials strewn across the interwebs)

Understanding the Grub 101:
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

SuperGrubDisk, a collection of automatic and manual functions:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by wizkid250 on 2009-08-14
im sorry, but i do  not understand what MBR is
could you point me to these tutorials?

---

### Post by LewRockwell on 2009-08-14
> **wizkid250 said:**
> im sorry, but i do  not understand what MBR is
could you point me to these tutorials?

Master Boot Record:
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

MBR tool for experienced users:
[http://download.cnet.com/MBRtool/3000-2248_4-10053458.html](http://download.cnet.com/MBRtool/3000-2248_4-10053458.html)

(grub information added to previous post)

.

---

### Post by berthiggins on 2009-08-14
You could try this................

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by LewRockwell on 2009-08-14
> **berthiggins said:**
> You could try this................

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

except that...that procedure installs the windows-only MBR...

and...it is interesting that the first comment to that article is to use SuperGrubDisk...

.

---

