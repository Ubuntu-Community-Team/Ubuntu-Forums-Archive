---
title: "HP Photosmart C6180 and wireless does nor work"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by pgiraudo on 2008-01-06
Hi,

I am struggling since some months (already under Feisty, now under Gutsy) to print on a HP Photosmart  C6180 printer, using a wireless connexion (hpsetup). Here I am:

+  I print, no problem, from  Windows XP (I have a multi-boot computer);

+ under Linux (Ubuntu Gutsy):

- I have proceeded all the setup steps described at: [http://ubuntuforums.org/showthread.php?p=1952834](http://ubuntuforums.org/showthread.php?p=1952834) and [http://ubuntuforums.org/showthread.php?t=452121](http://ubuntuforums.org/showthread.php?t=452121), and furthermore installed HPLIP libraries in their last version  (ver. 2.7.12) ;

- in Ubuntu, the 'hpsetup' wireless network is recognised and signaled active  (reception 97%);

However, the HP C6180 is NOT recognized (which is confirmed by hp-toolbox, see below).

When I try to print, the printer icon (top right of the gnome desktop) says "Not connected ? The printer "JetDirect" may not bee connected." ... although it is connected actually.

In short, I don't know how to go ahead to solve this problem.

Any hint welcome!

Patrick


PS: here below what I get running hp-setup:

giraudoux@giraudoux-laptop:~$ sudo hp-setup
[sudo] password for giraudoux:

HP Linux Imaging and Printing System (ver. 2.7.12)
Printer/Fax Setup Utility ver. 7.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

HP Linux Imaging and Printing System (ver. 2.7.12)
Services and Status Daemon ver. 9.3

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

---

