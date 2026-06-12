---
title: "Big Problem Can't access my windows 7"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by ahmed.hameed on 2011-05-17
Hi all 

my windows 7 doesn't open when i choose it from loader in ubuntu start up menu 

The story behind that was :I tried to reinstall my Ubuntu because i faced some serious problems,and by mistake when to choose the device to load the Ubuntu i choose the same device where windows 7 loader locate and when installation finished i got windows 7 refuse to startup then i tried to reinstall Ubuntu again and choose the right device in this time , but because my bad luck i corrupt the windows 7 loader as i think.


Any ideas to get my windows 7 back to start up again .!!!!  


Thanks

---

### Post by tkelito on 2011-05-17
What is manager your boot?  Grub or Windows Boot Manager (BCD)?  How are your partitions laid out?  Did you use Wubi or did you do the install outside of Windows?

Bit more details could help the case.

---

### Post by Prince Valiant on 2011-05-17
Since you're reinstalling Ubuntu anyway, I think the simplest method for making Win7 bootable again would be to reinstall Ubuntu (again :-D ).  I'm not sure if you did this before, but the main thing is to install grub to the HDD itself --choose the advanced option when you install, select where you want Ubuntu to go, and then worry about the proper location for Grub:

if you hard drive (HDD) is labeled sda (or sdb, or sdc, or hdb, or hda --you get the idea), then your partitions will be labeled sda1, sda2, etc (same goes for hda1 or sdc3).  Don't put Grub on the partitions; put it on the sda (or sdb, or hda, etc).

Does that make sense?  Hope that helps.

Have fun!

-Val

---

