---
title: "Grub Problems"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by Purist on 2009-11-20
Hi all.
I just installed Ubuntu 9.04 along side my Mac and windows partitions afew months back. I was very impressed by Ubuntu but there is a big problem. About a week ago, when I tried booting Ubuntu, a Grub screen came up saying "Grub". It freezes everytime I load windows or Ubuntu. I could only access my Mac partition so I burned a super grub disc. I tried booting the disk but it says "Loading stage 2" and freezes up. I managed to get onto Ubuntu with a grub rescue disk but I can't get onto my windows partition. I ended up erasing Ubuntu but I still can't boot windows. I'm not sure if I still have the code for it so I can't reinstall it. I also can't boot a windows recovery disk as it says booting in 3... 2... 1... but then it just says "Grub" and freezes. Does anyone know how to fix grub?

---

### Post by bodhi.zazen on 2009-11-20
You have to either repair your windows boot loader or re-install Ubuntu .

It sounds as if your computer is not booting to the CD , reboot your computer, as it is booting enter the BIOS and make sure it boots from the CD before the hard drive.

Boot the windows CD/DVD and fixmbr ;)

---

### Post by Purist on 2009-11-20
It can boot other CD's no prob but grub makes windows recovery disk unusable. Btw, I have no bios (Mac):D

---

### Post by bodhi.zazen on 2009-11-20
> **Purist said:**
> It can boot other CD's no prob but grub makes windows recovery disk unusable. Btw, I have no bios (Mac):D

Sounds like a problem with your windows disk as grub has no way of knowing what type of disk you are booting (grub is only loaded if booting the CD fails).

---

### Post by Purist on 2009-11-20
I'm not sure that its the disks problem as it worked when i removed grub from windows before.

---

### Post by bodhi.zazen on 2009-11-20
> **Purist said:**
> I'm not sure that its the disks problem as it worked when i removed grub from windows before.

Well, if you look at the boot process :

[http://www.ibm.com/developerworks/linux/library/l-linuxboot/](http://www.ibm.com/developerworks/linux/library/l-linuxboot/)

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-boot-init-shutdown-process.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-boot-init-shutdown-process.html)

You will see it goes 

BIOS -> CD

Not 

BIOS -> GRUB -> CD

---

### Post by Purist on 2009-11-20
I understand that but I dont understand why this isn't happening. Check [URL="http://yfrog.com/japhoto6ej"]http://yfrog.com/japhoto6ej
[/URL]

---

