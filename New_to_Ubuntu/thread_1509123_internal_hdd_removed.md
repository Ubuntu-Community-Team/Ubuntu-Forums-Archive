---
title: "internal hdd removed"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by DarinB on 2010-06-13
I used an extra sata hdd and installed it internally copied over my /home before installing lucid lynx lm9 got lucid lynx lm 9 running now fixed all the little bugs and stuff now i want to remove the old hdd and close the case but when i did that i got an error on boot can't find mnt/o and mnt/o1 the two partitions on that old hdd. I created those mount points at install.......it would not boot unless i plugged that old hdd back how can i remove it and have the boot go as if it were never there??????

---

### Post by oldfred on 2010-06-14
Post this and we can see what is sda & what is sdb.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by DarinB on 2010-06-14
good information but i already know what hdd it is i need to know how to remove it and not have my system search for it and not book.
I think i have to remove the mount points and edit the fstab but not sure about any of it or the order or the umounting thing first and don't know hoe to do that.
I know i can remove it by opening mnt as admin and i can delete mount points but not sure if that will mess things up.

---

### Post by DarinB on 2010-06-14
I got this reply from Taurus the Genius Staff Emeritus

If you decide to remove a drive from your machine, then you need to edit /etc/fstab and remove the entry for that drive.

From a terminal, Applications -> Accessories -> Terminal, fire up gedit with root privilege.

Code:

gksu gedit /etc/fstab

Save the changes. Shut down your machine and remove the drive that you don't need/use anymore. Then boot your machine and see if everything is working now.

Good luck.
__________________
In the world of Linux, who needs Windows and Gates...

Got most of my golden beans at an auction on eBay (with a couple of free drinks).

---

