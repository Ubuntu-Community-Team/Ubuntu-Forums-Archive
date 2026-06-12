---
title: "WD 1TB External HD does not open in Windows."
date: 2009-02-23
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-02-23
Strange problem...

I have a 320gb WD internal HD in my laptop (specs in signature). I also have a 100gb Hitachi (external) and a 1TB WD (external). When 

I have the 320gb internal partitioned in the following way:
100gb NTFS (Windows XP)
200gb Ext3 (/home)
10gb Ext3 (/)
3gb linux swap

I have the 100GB external partitioned the following way:
2gb NTFS  (file transfer and installation files)
98gb Ext3 (backup)

The 1TB WD external is partitioned the following way:
1TB Ext3 (Storage)

I use the following programs to be able to see the ext3 partitions in windows: [http://www.fs-driver.org/](http://www.fs-driver.org/). In general this program is great and easy to use.

However, I have a few problems with it:

I can read the following partitions when I am using Windows XP:
100gb NTFS (Windows XP)
200gb ext3 (/home)
2gb NTFS  (file transfer and installation files)
98gb Ext3 (backup)

Whenever I click on any of the other partitions I get the following message: "The disk in drive X is not formatted. Do you want to format it now?"

Why can't I read my 1TB ext3 external hard drive, and my 10gb partition with my / folder?

Thanks!

---

### Post by Ptero-4 on 2009-02-23
Do you have Ext2IFS set to automatically assign drive letters? IF not you can manually set drive letters to the HD's that gave problems and check the "assign drive letters automatically" checkbox. Also try and run fsck on the partitions from within linux.

---

### Post by abhiroopb on 2009-02-23
I have manually assigned all the letters. What will fsck do?

---

### Post by abhiroopb on 2009-02-23
I used gparted to do a graphical "check disk", it ran for 1.5 hours and I think it found some errors, etc. However, after booting into Windows XP and manually assigning a drive letter I still get the same message (about re-formating the drive).

Any suggestions?

Thanks,

---

### Post by abhiroopb on 2009-02-25
BUMP...

any more suggestions guys?

Thanks,

---

