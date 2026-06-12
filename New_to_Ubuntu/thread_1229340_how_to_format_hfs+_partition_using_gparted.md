---
title: "how to format hfs+ partition using gparted"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by ashish_envy on 2009-08-02
hey i m having an external drive of 500 gb of WD.
i want to format it wtih **hfs+** file system so that i can use it with my friends MAC note book. But i m not able to format it with hfs,hfs+ partition using gparted.............

when i go for the creation of the new partition and go to the option of file system............. it shows many option but it doesn't shows hfs+, hfs option..
i m able to make partition of ext2,ext3,ntfs,linux, fat 32, fat 16 ***BUT not with hfs, hfs+............***

please help me......
i m new to ubuntu please help me
how it is possible for me..................

---

### Post by 3rdalbum on 2009-08-02
Install the "hfsprogs" package in Synaptic.

---

### Post by Sef on 2009-08-02
Another option is to download [GParted]("http://gparted.sourceforge.net/").

---

### Post by 3rdalbum on 2009-08-02
> **Sef said:**
> Another option is to download [GParted]("http://gparted.sourceforge.net/").

> But i m not able to format it with hfs,hfs+ partition using gparted.............

Only when you install the "hfsprogs" package, does Gparted enable the option to format a disk/partition as HFS or HFS+. Try it and see.

---

### Post by sixit on 2012-10-15
> **3rdalbum said:**
> Install the "hfsprogs" package in Synaptic.

Three years later, your advice is still relevant and USEFUL!  Thank you! :D

---

