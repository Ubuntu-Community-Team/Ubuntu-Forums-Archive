---
title: "cant get the boot loader to go on, need help"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by DavideousAfarensis on 2010-03-08
whenever im turning on my laptop i get this message:

   GRUB loading
   error: unknown file system
   grub rescue>_

OK. My laptop has two operating systes, ubuntu 9.10 karmic koala, and windows xp pro. When I installed ubuntu recently and used Gparted for partitioning the drives I left an insufficient amount of space for xp. I became aware of this as I was working on xp, and received a message that i couldn't upload my photos because of lack of disk space. I download a drive partition wizard since i wasn't able to understand how to maneuver with the one which xp provides, and increased the size of the xp operating system partition. since i was sending commands from the same partition i was operating on, the laptop instructs me to allow a restart for partitioning to commence. i restart it, and the first thing that appears is the message above. and im stuck. please help.

---

### Post by steindor2 on 2010-03-08
> **presence1960 said:**
> Is your machine's BIOS capable of booting from USB? If so this is what I would do. I would restore Windows bootloader to MBR of sda, then I would put GRUB 0.97 on MBR of sdb & finally GRUB 1.97 on MBR of sdc (USB disk) this way that GRUB will take over when you boot from USB. I would also put GRUB 0.97 on MBR of sdb, then set sdb as first in the hard disk boot priority in BIOS. What that will accomplish is when you boot without the flash disk GRUB (0.97) from 9.04 will take over and you can boot Jaunty or Windows. If you boot with the flash disk GRUB 1.97 will take over and you can boot Karmic.

This how I would do it. Boot your XP install disk and do [this]("http://ubuntuforums.org/showthread.php?t=1014708"), following instructions for XP. Next boot the 9.04 Live CD/USB and choose "try Ubuntu without any changes", when the desktop loads open a terminal and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```When rebooting go into BIOS and set sdb (27GB) as first disk to boot in the hard disk boot order. Save changes to CMOS and continue booting into Ubuntu 9.04. Open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```scroll down the bottom and change the windows entry to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader    +1
```Note sda becomes (hd1) because you just switched it prior to second in hard disk boot order in BIOS!
Click Save at the top on the toolbar & close file. Reboot and see if you can boot into windows. If successful you can now put GRUB 1.97 on MBR of sdc.

see this: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)


do this:D

---

