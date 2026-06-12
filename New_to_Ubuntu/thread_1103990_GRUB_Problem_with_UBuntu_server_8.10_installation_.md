---
title: "GRUB Problem with UBuntu server 8.10 installation on an externa drive disk"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Feidias on 2009-03-23
Dear Friends,

This threa is connected with a previous post I have made with Kubuntu GRUB, but because I can't work on my laptop at all I post it again here...

I have tried to install ubuntu-8.10-server-i386.iso, on an other external drive disk on the previous laptop.

When I have been asked where to install GRUB i didn t install on MBR but I have installed it on one of the partitions the (hd0,1).

The problem is that GRUB is loaded only when I plug the external drive disk.

On the other hand I can't load Windows, it goes to GRUB stage 2 and restarts GRUB stage 2. When I choose Windows option it loads GRUB again.

Also, ubuntu is loaded on a console. Not on a graphical mode.

I have tried Windows Recovery Console "fixmbr" but nothinng happened.

I have tried to write the grubboot.lin file to an external USB as  user [COLOR="Black"]dandnsmith[/COLOR] proposed me on a previous thread with the command:

dd bs=512 count=1 if=/dev/sda of=/media/sdc1/grubboot.lin

and I take the message:

/dev/sda permission denied

Another person I have asked was able to load multiple LINUX editions on a hard drive disk.How is that possible?

How can I restart Windows and fix this problem?

I have also seen that there is a choice on the boot menu to modify grub by pressing 'c'. Do you any procedures?

Any help would be priceless...

Thanks again

---

### Post by e_james on 2009-03-23
I am confident that, if I was in your position, I could fix the situation in a few hours of head scratching with the help of some forum searches and the grub manual  ---  [http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

This is what I think I know.
In most recent PCs there is a way to select alternative boot options such as CDs, usb flash drives etc. without modifying the bios boot priorities.
This is what I use on my eee PC 901. Grub is installed in one of the partitions of the second solid state drive. If I do nothing, the computer boots the standard Xandros desktop. If I press the escape key as the bios starts, I get an option list where I can start the alternative grub and boot Ubuntu. 

The main effect of the grub installation is to tell the grub code in the boot record where to find the kernel files or the next bootloader (Windows). Sometimes to get grub to start Windows properly it is necessary to add "hide" and "unhide" commands to the grub menu. I have also recently discovered that Windows XP won't start unless it is in the number 1 position of the partition table. It doesn't have to be the first physical partition, but it must be number 1. 

The main grub files are stored in "/boot/grub", so if the drive containing this directory is not present, grub can't start.

Sometimes grub gets installed with slightly incorrect menu details. If you have an idea what is wrong you can press "e" at the grub menu and fix the relevant line. When you get it right, you can then edit the grub menu file "/boot/grub/menu.lst" to make it permanent (at least until the next kernel update).

I suspect the "permission denied" message is because you didn't execute the command as "root". Try putting "sudo" in front of it. E.g. the menu edit command is "sudo gedit /boot/grub/menu.lst".

With a few searches you should be able to find detailed instructions for restoring the standard Windows boot code to the MBR if necessary.

It is possible to have multiple installations of Ubuntu or other Linux, and even more than one Windows, on a sufficiently large hard drive but the complication is that each will install a boot loader. The trick is to do it in the correct order and in the right positions. In general, Windows should be first and Ubuntu should be last. Modern PCs have the capacity to run virtual operating systems as an alternative to dual booting. You can run Linux within Windows and Windows within Linux.

---

