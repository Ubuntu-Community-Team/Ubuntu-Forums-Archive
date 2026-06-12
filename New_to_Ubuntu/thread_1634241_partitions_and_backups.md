---
title: "partitions and backups?"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by gmenfan83 on 2010-11-30
I am very confused on this topic can someone please direct or explain to me in English about partitions and how the act with backups ....I have windows and Ubuntu on my laptop and want to make backups of both and make sure I have a good amount of space on each what I think would be partition and if not then reallocate to do so

---

### Post by Rubi1200 on 2010-11-30
Read these links and then post back if you have more questions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://clonezilla.org/](http://clonezilla.org/)

We would also need to know how much disk space you have and which versions you are running.

Thanks.

---

### Post by gmenfan83 on 2010-11-30
> **Rubi1200 said:**
> Read these links and then post back if you have more questions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://clonezilla.org/](http://clonezilla.org/)

We would also need to know how much disk space you have and which versions you are running.

Thanks.

Thank you I will read up and post back my disk space when I get home to my computer and I am running Ubuntu 10.10 32 bit and vista for windows

---

### Post by gmenfan83 on 2010-11-30
ok so i downloaded gparted and attached is a screen shot of my partitions.......i see i have a few including an extened partition ...i only have windows and ubuntu should i have these extra partitions?

---

### Post by gmenfan83 on 2010-12-01
bump please:p

---

### Post by Linux_junkie on 2010-12-01
> **gmenfan83 said:**
> ok so i downloaded gparted and attached is a screen shot of my partitions.......i see i have a few including an extened partition ...i only have windows and ubuntu should i have these extra partitions?

Having looked at your screen dump I can tell you that the first three partitions relate to Windows and the final two relate to Linux.  Do not worry this is normal set up.

In answer to your question about partitions and backups.  A partition is simply a part of a disk (usually hard disk) that has been set up to make the OS think its using two or more disks rather than just the one.  Partitions are set up to protect your files from corruption or accidentally wiping your disks.  

Backups are simply copies of files / applications you want to keep and recover should something like corruption takes place.  There are many ways to make copies of files and apps.  From simply copying the files to a disk big enough to store it to using a file compression utility to using specialist backup software.

Hope this has answered your question

---

### Post by QLee on 2010-12-01
Looks normal to me.
Two primary partitions; sda1, Toshiba System Volume (you have a Toshiba computer, eh?); sda2, Windows.
One extended partition, which is the container for sda5, Ubuntu and sda6, the swap partition for Ubuntu to use.

---

### Post by gmenfan83 on 2010-12-01
thank you guys so much for clearing this up for me ....i just want to be sure ...i get ocd about understanding stuff i dont and knowing whats on and the ins and outs of my system

---

### Post by Rubi1200 on 2010-12-01
I agree with the assessments of the users who posted previously. 

Your setup looks quite normal and the only thing you need to do is take care to make regular backups of your data and always have an Ubuntu LiveCD and a Windows installation/recovery CD available.

---

