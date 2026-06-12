---
title: "Moving to trash from external drive"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by Andy06 on 2009-06-16
Any files I delete or select "Move to trash" are never moved to trash and are instead deleted outright (it warns and gives me the option to that).

But why can't I move it to trash? I know external drives have their own trash but it doesn't delete to that either. Something to do with drive permissions?

Also how many trashes should I be looking out for? gksudo nautilus sends everything to the root trash right?

---

### Post by Dr Belka on 2009-06-16
I have this issue as well

---

### Post by PureLoneWolf on 2009-06-16
I have only experienced this if the external drive is NTFS or FAT32 - I must confess I just assumed it to be a limitation of using these file systems within Ubuntu - I have one ext3 formatted external drive and I don't get this problem

---

### Post by kpkeerthi on 2009-06-16
It should be in a **hidden** folder **.Trash-<user>** on the external drive. 

If your external drive is mounted as /media/disk, the trash folder would be /media/disk/.Trash-<user>.

---

### Post by Andy06 on 2009-06-16
I have hidden folders enabled, there is no such folder.

Anyway, that is considering it is normally deleted and I don't know where it went. THEN it goes into that hidden folder.

My problem is it notifies me that this file cannot be moved to trash and asks me to allow it to delete permanently.

BTW, my drive is indeed NTFS formatted. So only ext formatted drives can delete to trash in Linux?

---

