---
title: "Vista, Backtrack 3, Ubuntu"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by khubliakhan on 2008-12-27
OK - Linux noob here needing help,

I have installed the Vista, Backtrack 3 and Ubuntu GParted is giving the following info:

/dev/sda1        Vista
/dev/sda2        Extended
    /dev/sda5    /boot
    /dev/sda6    Backtrack is installed here
/dev/sda3        SWAP 2048
/dev/sda4        Ubuntu is here

I can boot into Vista and Ubuntu no probs but I think Ubuntu formatted the /boot drive which was supposed to be for Backtrack. I thort Ubuntu would recognise the boot and configure it automatically as it did for Vista.

I want to be able to boot into Backtrack - any advice as to what I can do? I think changes are needed for the menu.lst file in Ubuntu but am somewhat confused as to what should be written.

Any ideas help gratefully appreciated!!!

---

### Post by nhasian on 2008-12-27
i think the super grub disk can help you:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems)

---

### Post by 2hot6ft2 on 2008-12-27
Check the remote-exploit forums for backtrack3. You have to manually add it to the menu.lst

---

### Post by 2hot6ft2 on 2008-12-27
Here's an install there that should help you figure it out. [http://forums.remote-exploit.org/showpost.php?p=37268&postcount=1](http://forums.remote-exploit.org/showpost.php?p=37268&postcount=1)

---

