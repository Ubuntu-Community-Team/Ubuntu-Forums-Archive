---
title: "can't boot after erase of linux partiton, get terminal like screen"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by db4sn3r on 2009-05-26
hi I am on a samsung nc10 that was booting 9.04,windows 7, and recently installed the new moblin os, I wiped the moblin partition because it wasn't working very well, know when I boot I get to a GNU GRUB terminal and can't acess aqny of my partitions,  I ned a way to boot into my windows partition, I can't remember what the path to my windows boot loader, or linux, I am pretty sure nothing was deleted, what should I type nto the terminal to get to my windows partition, is there a way to get it to list the boot partitions/what their path is??? if I reinstalled linux, would that give me grub, and because of grub allow me to boot into windows 7??? please help!

---

### Post by logos34 on 2009-05-26
Download the [Parted Magic LiveUSB]("http://partedmagic.com/documentation/130-creating-the-liveusb.html"). Or use an Ubuntu live usb if you have one

Boot the desktop, open a terminal and type in the commands as explained in the link below in my signature "Restore Grub..."

What happened was when you added Moblin it replaced ubuntu grub with it's own pointing to it's own menu.lst on / partition.

---

### Post by ajgreeny on 2009-05-26
As I understand things, you still have your ubuntu 9.04 install.  If that is so, follow the link mentioned by the previous poster in this thread on how to [reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351") back to ubuntu.
Should you no longer have ubuntu installed you will need to use your windows install CD (not a recovery disk) or use [supergrub]("http://www.supergrubdisk.org/").
> ...... with the objective of repairing the MBRYes. Sorry I missed that bit out!

---

### Post by candtalan on 2009-05-26
> **ajgreeny said:**
> As I understand things, you still have your ubuntu 9.04 install.  If that is so, follow the link mentioned by the previous poster in this thread on how to [reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351") back to ubuntu.
Should you no longer have ubuntu installed you will need to use your windows install CD (not a recovery disk) or use [supergrub]("http://www.supergrubdisk.org/").
...... with the objective of repairing the MBR

---

### Post by db4sn3r on 2009-05-26
Thank you guys so much it is working now!!!! I am so glad I didn't get rid of my live cd!

---

### Post by logos34 on 2009-05-26
you have a cdrom on a netbook?

---

