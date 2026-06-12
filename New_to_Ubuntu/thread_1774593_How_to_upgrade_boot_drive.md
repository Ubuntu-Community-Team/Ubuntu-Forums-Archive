---
title: "How to upgrade boot drive??"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by petermg on 2011-06-03
I have what I think may be a failing boot drive, which is my only Ubuntu drive, and I would like to replace it with a newer and larger one.  Is there a way I can do this without having to reinstall Ubuntu and redo all my personal settings for hardware/software from scratch?

---

### Post by candtalan on 2011-06-03
> **petermg said:**
> I have what I think may be a failing boot drive, which is my only Ubuntu drive, and I would like to replace it with a newer and larger one.  Is there a way I can do this without having to reinstall Ubuntu and redo all my personal settings for hardware/software from scratch?

I would usually consider 
clonezilla (live cd) for this sort of thing

[http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)
I prefer to work using images of drives first saved to a third drive, because there is less chance of getting the from and to drives mixed up - can be an easy but disastrous mistake

If the drive is failing fast,then consider backup of critical data early first.

You are aware of the disc utility in Ubuntu I expect?
system>administrator>disc utility

good luck

---

### Post by YesWeCan on 2011-06-04
Quick way...
Attach your new disk - must be at least as big as the old one
boot off live CD
**sudo fdisk -l**
to find out what the drive letters are.
Say the original is sda and the new is sdb
**sudo dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror**
wait until done; could take an hour or more depending on disk size
Shutdown, remove old disk. Boot off new disk.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

