---
title: "cannot boot windows"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by chong601 on 2010-08-14
Hey guys,

I have recently installed ubuntu on my 40 GB hard disk and I had deleted the ubuntu by deleting the partition because it was not so suitable for my computer. (I think I made a big mistake....)

But, my computer cannot boot windows because I did not delete the grub from the sda1.

How to delete it......... I missed my Windows XP........................

---

### Post by wilee-nilee on 2010-08-14
If you just need the MS bootloader put in sda=mbr here is a link.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

If you need a link to a  XP ISO mention it.

---

### Post by skarme on 2010-08-14
> **chong601 said:**
> Hey guys,

I have recently installed ubuntu on my 40 GB hard disk and I had deleted the ubuntu by deleting the partition because it was not so suitable for my computer. (I think I made a big mistake....)

But, my computer cannot boot windows because I did not delete the grub from the sda1.

How to delete it......... I missed my Windows XP........................
The issue is simple to resolve. Since you don't need Ubuntu anymore all you have to do is insert your Windows Xp setup CD and enter recovery console.
Once you're there, select your OS and enter you're password. (Just press enter if you haven't entered any password)
Now type:
```

fixmbr

```You'll see a warning. Press 'y' and enter. Now restart you're PC.
GRUB will disappear and you'll boot straight into Windows XP.
Check this link in case you're in doldrums after reading the above. :P
[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

---

### Post by LewRockwell on 2010-08-14
Super Grub Disk can fix master boot records as well.

Probably easier than finding those recovery disks that the majority forgot to make.

[http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)

.

---

### Post by chong601 on 2010-08-16
> **LewRockwell said:**
> Super Grub Disk can fix master boot records as well.

Probably easier than finding those recovery disks that the majority forgot to make.

[http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)

.

I don't know how to set up the SGD.........

---

### Post by chong601 on 2010-08-23
> **wilee-nilee said:**
> If you just need the MS bootloader put in sda=mbr here is a link.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

If you need a link to a  XP ISO mention it.

I think i need to download an ISO image........

---

