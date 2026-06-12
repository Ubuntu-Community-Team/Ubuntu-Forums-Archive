---
title: "Manually install boot loader?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by MSich on 2010-12-22
I have a dual boot system with XP.  It was running 9.10 and was upgraded to 10.04 several months ago.  While running 10.04 the laptop was dropped.  After that grub stated no file system found, but would continue to the grub menu and the XP system would still load and operate normally.

Tonight I decided, since I didn't really have anything critical on the Ubuntu system, that I'd delete those partitions and load 10.04.1.  

During that installation, I may have not setup the Linux partitions correctly in the free space.  FYI

At the end of the installation, it encountered an error loading the boot loader.  I checked to manually install the loader (hoping that the existing grub2 would at least load XP if nothing else.

However, not when I boot it comes to a   grub rescue>  prompt and I can get no further.  Interesting enough, I cannot even boot from the CD now, as it spins and spins and then comes to the same prompt.

How can I manually install grub so I can continue?

Thanks

---

### Post by MSich on 2010-12-22
I found the mega thread on grub rescue.  Using that info I found my grub folder on (hd0,6).  It was currently set to (hd0,5) for both prefix and root.  I changed those and tried to run insmod.  I had no luck, so I did ls /boot/grub  and the folder is empty.  All other drives listed using ls return a file system error.

---

### Post by wilee-nilee on 2010-12-22
If it is just XP grub wont work. You need a XP install cd booted and in the repair command line just run.
/fixmbr.

Or a Ubuntu live cd to install lilo with lilo will boot XP.

First boot the Ubuntu live cd run in the terminal.
sudo fdisk -lu
your just confirming if the hd is being read as sda, or any letter, no numbers following, then run these command with the correct HD sda, sdb, what ever it is.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

If you found any grub in XP then do this. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

