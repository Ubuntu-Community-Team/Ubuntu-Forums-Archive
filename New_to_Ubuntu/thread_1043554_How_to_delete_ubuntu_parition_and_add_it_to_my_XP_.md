---
title: "How to delete ubuntu parition and add it to my XP without recovery CDs"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by CeBiff on 2009-01-18
Hi,

I recently tried dualbooting windows XP and ubuntu on my laptop, but wireless proved to be too much work so I'm sticking to using ubuntu on my desktop and XP on my laptop.  The thing is, I don't ahve my XP CDs anymore, and I want to delete my ubuntu partition and add it to my windows xp partition.  I could just delete the partitions and add them to XP, but if I do, I mess up the boot.ini/grub/etc and have to do the fixmbr thing, but I don't have my XP CDs, so I can't do that.

Is there any way to delete hte ubuntu partitoin?  Or at the very least, shrink it and add the space to my XP partition without messing up the boot.ini/grub/etc?

Thanks

---

### Post by mikewhatever on 2009-01-18
You can easily delete partition with gparted live cd, but before you do that, make sure to fix the mbr for Windows.

---

### Post by CeBiff on 2009-01-18
Do you mind giving me some quick steps as to how to do that?

Sorry

---

### Post by adult swim on 2009-01-18
you might want to look at the super grub disk
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
as it can restore a windows mbr

---

### Post by CeBiff on 2009-01-18
Is there anyway i can use gparted to expand windows and decrease ubuntu without altering my grub/mbr/boot.ini etc?

---

### Post by adult swim on 2009-01-18
EDIT: i didnt read what you wrote correctly.  you can do that as diablo has mentioned but it will take a looooong time.

---

### Post by diablo75 on 2009-01-18
> **CeBiff said:**
> Is there anyway i can use gparted to expand windows and decrease ubuntu without altering my grub/mbr/boot.ini etc?

Gparted can do that in a jiffy.  Just boot up the livecd and resize as desired.  All you have to do is right click on the Ubuntu partition and select resize.  You can then shrink it down, move it to the left or right to make space for the Windows partition, and then resize the Windows partition to fill in the empty space.  It'll take forever, but it should work.

---

### Post by mikewhatever on 2009-01-19
> **CeBiff said:**
> Is there anyway i can use gparted to expand windows and decrease ubuntu without altering my grub/mbr/boot.ini etc?

Yes, but if you delete the Ubuntu partition, GRUB wouldn't work any more.

---

