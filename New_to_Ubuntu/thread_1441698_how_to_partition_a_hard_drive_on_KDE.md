---
title: "how to partition a hard drive on KDE"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by 007casper on 2010-03-29
in order to partition an additional hard drive on gnome I know you could go to system > administration > partition editor.  

How do you achieve this on kde?

Thank you.

---

### Post by inobe on 2010-03-29
open packagekit ans search for **partitionmanager**



Partitionmanager allows you to manage your disks, partitions and file systems. It has the ability to create, copy, backup & restore partitions through a KDE interface while supporting many different file systems (ext2, ext3, NTFS, FAT32, reiserfs & more).

---

### Post by srs5694 on 2010-03-29
You can run exactly the same programs in KDE as you can in GNOME, with the exception of little applets that are part of the KDE or GNOME environments. AFAIK, no partition manager falls into this category. Thus, it's just a question of locating the program in your menu or, failing that, launching it from a command line. In the case of GParted, the command-line command is "gparted," so you can type that (probably preceded by "sudo" or a GUI equivalent, such as "gksudo") to launch GParted. The text-mode fdisk (or gdisk for GPT disks) tools run in a Terminal, Konsole, xterm, or whatever equally well in both environments, too.

---

### Post by 007casper on 2010-03-30
partitionmanager crashes on load.  I logged out, log in.  No hope.
> Executable: partitionmanager-bin PID: 11989 Signal: 11 (Segmentation fault)

I have tried gparted through terminal it loads.  Now, I have both of them.  I dont know if that will be a problem.

---

### Post by D.Bon on 2010-03-30
I installed partition manager but on starting it asks for  the password and when I give it the password nothing happens it just doesn't start...then it started later but I couldn't delete the post sorry

---

