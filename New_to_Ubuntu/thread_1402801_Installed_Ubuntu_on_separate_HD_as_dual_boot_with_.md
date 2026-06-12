---
title: "Installed Ubuntu on separate HD as dual boot with XP - now can't boot XP or Ubuntu"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Nermi on 2010-02-09
My computer:
Pentium Dual-Core CPU
E6300 @ 2.80GHz
2GB RAM
XP SP3
2 X 500GB SATA HDD's
Motherboard: P5Q-EM DO

I added 500 GB IDE (PATA) HD to this configuration and installed Ubuntu 9.10 on this drive. My intention was to create a dual boot XP/Ubuntu on the same system. 

Installation went without problems, but when I rebooted and expected to see GRUB manager and option to chose between operating systems, all of sudden Windows logo shows up and XP apparently trying to boot. Then it goes to restart and the black screen pops up with "We are sorry for inconvenience... " message asking me if I wanted to "start Windows normally". If I do that, I get the same thing again and again in a loop. 

So, at this point I can not boot either XP or Ubuntu on that machine. 

Can anyone help?

Thanks.

---

### Post by Sceiron on 2010-02-09
Pull out one disk and power up the comp.
If its not working plug it back, pull out the other, and power up.
Hopefully you will be able to boot one of the systems....

Google:
site:ubuntuforums.org dual boot two Hd

Edit:
You expected to see Grub ---> by installing Ubuntu on the second hard drive, the Grub bootloader maybe ended up on this hard drive.
(did you disconnect the XP disk when installing ubuntu?)

SO when you power up, the XP disk is the primary disk in BIOS, and therefore loads windows?

---

### Post by oldfred on 2010-02-09
Depending on BIOS you may be able to reset boot order BIOS. Old IDE drives booted from the primary master and BIOS just used that. New SATA drives are all controlled in BIOS as to boot order. Systems may let you change boot order. Set second drive to first in BIOS and see if it boots. You may still have to run repairs on windows as grub will only boot to a working windows. With windows drive first it should boot. If not you can run repairs from a windows CD. 

Your windows drive may have been renumbered as some BIOS make the IDE drive first in the drive chain. Then the boot.ini in windows is not drive 1 but drive 2.

Boot order is not the order the system see them which is usually the order they are plugged into the SATA ports. Adding an PATA then may be first or last?

If you want to see your entire configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by albert s on 2010-02-09
I done something a little bit similar a while back, except I just had ubuntu booting.
it was easier for me to just re-install ubuntu again, and set that HD as the primary boot one.
I had unplugged the other disc /s when I installed the different OS 's.

---

