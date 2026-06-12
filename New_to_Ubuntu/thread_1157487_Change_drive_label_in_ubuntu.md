---
title: "Change drive label in ubuntu?"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Dr.Vista on 2009-05-12
I've tried searching but no solutions. The only way the works for me is install Gparted and changing the drive name there. Is there an alternative way?

---

### Post by Dill on 2009-05-12
Check out this: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

I believe you can also edit your fstab to change the drive label (among other things) upon mounting: [https://help.ubuntu.com/community/Fstab#Useful%20Commands](https://help.ubuntu.com/community/Fstab#Useful%20Commands)

Cheers,
Dill

---

### Post by logos34 on 2009-05-12
ext2/3/4:

sudo apt-get install e2fsprogs

> sudo tune2fs -L <label> /dev/sdxy

or 

> sudo e2label <device> <label>

reboot may be necessary before the label appear on desktop or browser side pane

---

