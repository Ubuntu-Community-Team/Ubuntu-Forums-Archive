---
title: "Adding a label to partitions"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-12-06
After recently doing a fresh install of 9.10, I find that some of my partitions are shown in nautilus and elsewhere with very odd names. This is my output of sudo blkid:
```
:~$ sudo blkid
/dev/sda1: UUID="A2401BBF401B995D" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="CEA61E2BA61E1515" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda4: UUID="DC0E219E0E2172A6" LABEL="DATA" TYPE="ntfs" 
/dev/sdb1: UUID="7551d527-6cc4-4f42-9f68-7d2cead50e3c" TYPE="swap" 
/dev/sdb2: UUID="688df683-e46e-4be5-8979-0d850c67d15a" TYPE="ext4" 
/dev/sdb3: UUID="e8714d41-bba5-4764-bb96-957fa7b188a1" TYPE="ext3" 
/dev/sdb4: UUID="7F2A3353027874FC" TYPE="ntfs" 
```

I'm happy with the names of sda1, sda2 and sda4, and I don't see any point in naming sdb1 or sdb2. 

However, I'd really like to add a sensible label for sdb3 and sdb4 to avoid nautilus just showing them by their incomprehensible UUIDs.

I'd like sdb3 to have the label "OLDHOME", and I'd like sdb4 to have the label "52Gb".

Could someone tell me how I do that please?

---

### Post by Zoot7 on 2009-12-06
You can change the label in Gparted, just right click on the drive, change it, and then click apply.

---

### Post by Gr8world on 2009-12-06
You can add labels with gParted. 

Just right click on the drive (make sure it's not mounted) and the click on label.

This worked for me.

---

### Post by Gr8world on 2009-12-06
Oh sorry Zoot7, didn't see your post...

---

### Post by Zoot7 on 2009-12-06
Haha, no worries.

---

### Post by SuperSonic4 on 2009-12-06
> **zoot7 said:**
> you can change the label in gparted, just right click on the drive, change it, and then click apply.

+1

---

### Post by Roger Allott on 2009-12-06
Thanks for the responses. I've been able to add a label to sdb3, which is ext3, but gParted wouldn't allow me to add a label to sdb4, which is NTFS.

---

### Post by efflandt on 2009-12-06
Name the ntfs partition from Windows.  Just go to My Computer, right click on it, and rename it.  Note that by DOS convention, it ends up 11 characters maximum and capitalized (whether you use upper or lower case to enter it).

---

### Post by Roger Allott on 2009-12-06
> **efflandt said:**
> Name the ntfs partition from Windows.  Just go to My Computer, right click on it, and rename it.  Note that by DOS convention, it ends up 11 characters maximum and capitalized (whether you use upper or lower case to enter it).

Thanks. That did the trick. I'm surprised though that one cannot do that in Ubuntu.

---

### Post by Zoot7 on 2009-12-06
Windows is always the best tool to play with Ntfs partitions really.

---

