---
title: "hard disk settings for virtualBox"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by nachos99 on 2009-03-01
im trying to install XP inside virutalBox.

i dont know if this is relevant but im currently dual booting XP and ubuntu. XP is on my primary IDE master and ubuntu is on my SATA drive.

i have not yet gone through with the XP installation in virutalBox; im still at setup.

after going through the set up the first time, i noticed that under hard disks settings it had it as IDE primary master for slot and windows.vdi (Nrmal, 15.00 GB) for hard disk.

im wondering if that means it's going to try to write to my windows IDE hard drive.  

should that be changed to SATA port 3 in order to write to by ubuntu HDD?

or is it just than when it says IDE primary master, is that a virtual IDE primary master and not my actual IDE primary master (which is just windows and i dont want virtualBox writing onto it)?

thanks for any clarification.

---

### Post by freakyzoidberg on 2009-03-01
its indeed a virtual IDE disk pointing to the .vdi file

Virtualbox would not touch to your disk physically, no worries ;)

---

### Post by nachos99 on 2009-03-02
virtual XP was set up in the virtual IDE but written on my actual SATA.

just like you said.  thank you.

---

