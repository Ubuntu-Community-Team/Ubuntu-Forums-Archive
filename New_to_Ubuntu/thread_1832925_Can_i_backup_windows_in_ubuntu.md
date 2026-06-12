---
title: "Can i backup windows in ubuntu"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by fattony1968 on 2011-08-25
My laptop crashed  and i'm running ubuntu from CD is it possible to backup my windows files before i fully install ubuntu as my operating system instead of recovering microsoft operating system.
Cheers in advance for any help

---

### Post by seawolf167 on 2011-08-25
Sure! You can use any number of [methods ]("https://help.ubuntu.com/community/BackupYourSystem")to back up like [rsync]("https://help.ubuntu.com/community/rsync"). I, however, suggest that you make a disk image using [Clonezilla]("http://www.clonezilla.org"). This way you can restore everything to its original settings (including the MBR, etc.) in case something goes wrong and you want to start over/try again.

Note that since you are in a LiveCD environment, you can simply plug in an external hard drive and copy/paste your critical Windows documents, images, videos, etc. over to the external drive.

---

