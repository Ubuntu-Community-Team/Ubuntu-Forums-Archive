---
title: "Where do I get super grub CD now?"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by anewguy on 2010-08-17
I did a dumb thing (I know better but had a brain fart tonight).  Somehow I managed to wipe the contents of my Windows and Ubuntu partitions off my netbook's harddrive, but grub remains in the mbr.  I wanted to restore the netbook using its built-in recovery, but grub comes up and fails.  So, next I restored using the restore CDs I made (glad I made them).  Again, at boot, grub comes up and fails.  Using an ubuntu LiveCD and can see it did recreate the Windows XP partition, but with grub gone I can't boot.  Trying the "Boot from hard disk" option on the LiveCD just gives me the grub error again.

I know if I had an actual Windows XP disk I could restore the MBR quite quickly, but there is no such thing with this netbook - just the recovery partition and the restore disks.  So, I went looking around and it appears that the super grub disk is supposed to let me actually boot a partition even if the MBR is messed up.  So, I went looking for super grub - found the supergrub site and it is all messed up like someone was playing around at creating a website and never finished it.  Went to (I think) freshmeat something and found super grub there, but it downloads as a .bz2 file - I'm on Windows on my desktop right now so I can't access that file either.

Any help on pointing me to a super grub disk image I can work with in Windows, or for that matter any way to restore the Windows XP MBR without the Windows disk would be greatly appreciated!

Thanks!
Dave ;)

---

### Post by Elfy on 2010-08-17
How odd - looked ok the other day.

I have a copy of it here - if you PM me an address I can send it to you.

---

### Post by JBAlaska on 2010-08-17
Here's a [Link](http://developer.berlios.de/project/showfiles.php?group_id=10921) to super_grub_disk_hybrid-1.98s1.iso

---

### Post by anewguy on 2010-08-17
> **forestpiskie said:**
> How odd - looked ok the other day.

I have a copy of it here - if you PM me an address I can send it to you.

Thanks!  That and a quick run of the free program mbrfix did it!

Dave ;)

---

