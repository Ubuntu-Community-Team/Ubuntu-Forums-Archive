---
title: "Is it possible to format a system drive ntfs?"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by bettyhills on 2010-02-02
Is it possible to format a Fat32 Ubuntu system drive to ntfs leaving the program and data undisturbed?

I created a gparted liveCD and used it to format a slave drive to ntfs.  It worked perfectly.

Can the gparted liveCD be used on the master drive similarly without destroying the existing files on it?

---

### Post by egalvan on 2010-02-03
I don``t think the formatting tools have the capability of doing a ``non'destructive`` format.

Windows itself has a conversion tool, that converts a drive from FAT to NTFS.

Personnaly, I don´`t trust these tools...
I back-up before using anything like this.
Or partition, or format.

---

### Post by nhasian on 2010-02-03
the best way is to backup all the data from the fat32 drive onto an external hard disk or a different partition from the one you are reformatting.  once you've backed up your data you can have gparted delete the fat32 partition and create an NTFS partition (or any other filesystem for that matter).  Then copy your files back.

---

