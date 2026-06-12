---
title: "saving system configuration"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by pendulum101 on 2009-05-04
does anyone know of any way that i can save my ubuntu configuration to a usb or a cd because i want to reformat my hard drive to increase the allocation for ubuntu and i also want to install windows 7 along side it , thanks in advance

---

### Post by mike555 on 2009-05-04
You could try "remastersys" , it lets you make a remastered cd/dvd of your ubuntu install , including setup (if you tell it to).......

---

### Post by pendulum101 on 2009-05-04
> **mike555 said:**
> You could try "remastersys" , it lets you make a remastered cd/dvd of your ubuntu install , including setup (if you tell it to).......

where would i get that is it a program or a function in terminal

---

### Post by apienk01 on 2009-05-04
Do you have your /home on a separate partition? Or you have installed the whole ubuntu just on one partition? Having a separate partition makes such operations a lot easier to do.

All your settings and personal files are located in your /home directory. The settings are mostly in hidden directories whose names begin with a dot (you can see them by pressing Ctrl-H in Nautilus file explorer). To save settings just copy somewhere your entire /home directory.

EDIT: You do not have to format your hard drive. Just boot with Ubuntu LiveCD, and run gparted (partitioning program). Then resize your partition as you wish. Your files will be left intact (but remember not to tick "format"). If you plan to install Windows on a separate partition, be aware that it will overwrite your GRUB (bootloader), and Ubuntu will not boot anymore. To fix it and get a proper dual-boot menu you will have to repair GRUB with Ubuntu LiveCD.

---

### Post by pendulum101 on 2009-05-04
ya ill do that thanks for the info will i be able to save it to an external hdd.

---

