---
title: "Grub fail, Error 24"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by POWMS on 2009-06-10
Hello all,
last night after installing Open Office 3.1 tarball, my system crashed with a series of file errors showing up on the screen. Rebooting the comp I got a Grub failed, and Error 24. When I used the Super Grub disc to try and repair the grub, I get a Grub failure and Error 15. So I cannot even get to safe mode to do any repairs.
Option 1: is the grub repairable given the errors?
Option 2: a good time to do a fresh install (upgrade) to 9.04?
I regularly back up my files so no great loss to wipe the hard drive.
Regards.

---

### Post by lindsay7 on 2009-06-10
The grub error codes you got are for,

24 : Attempt to access block outside partition
    This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool). 


15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

Can you type into the terminal these two things and post them here

sudo fdisk -l  (the letter l)

and

sudo gedit /boot/grub/menu.lst

---

### Post by POWMS on 2009-06-10
lindsay
comp won't boot so I can't get to the terminal.
Regards.

---

### Post by Miljet on 2009-06-10
Sounds like a very good time to upgrade (fresh install).

---

### Post by POWMS on 2009-06-11
Miljet
I did just that last night.Xubuntu 9.04 Jaunty Jackalope is superb......each upgrade just gets better and better (as it should!).
I can't wait for the next upgrade.

---

