---
title: "installed ubuntu, windows 7, there is no dual boot"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by mlotfi on 2010-04-12
Hi,
I installed ubuntu 9.10 first, then windows 7, when I restart the computer, it start always windows 7, I don't have the option to choose between ubuntu and windows 7.

can you plz help me.
thanks,

---

### Post by e4uforums on 2010-04-12
Can you give some more information on your setup?  Are you using a single drive or multiple drives?

If you have just a single disk, and if you chose the default options when installing Windows 7, it would have completely overwritten the Ubuntu install.  By default, Win7 will use the entire disk.

---

### Post by Mark Phelps on 2010-04-12
Boot from an Ubuntu LiveCD, open a terminal, and enter "sudo fdisk -lu"  (that's a lowecase L, not a one).  That will tell us what partitions are present on your drives.

---

### Post by ranch hand on 2010-04-12
Or just follow these directions from your Live CD;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the directions about file editing as that will be taken care of by "update-grub" and the "grub-install" command will put grub on your MBR.  If you are on mor than one drive run the install command for each drive.

---

