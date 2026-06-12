---
title: "nVIDIA drivers in Ubuntu 10.10 - black screen"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by x6herbius on 2011-02-27
I'm fairly new to Linux and am at my wits' end trying to get the nVIDIA drivers to work correctly.

I have an HP Pavillion tx1000 laptop with an nVIDIA GeForce 6150. After a fresh install of Ubuntu 10.10 x86_64 the GUI is displayed fine, and after updating to the recommended nVIDIA drivers through the hardware utility and restarting it still works. However, after a further restart, the computer will play the login sound but the screen will stay black. I can get into a terminal with Ctrl-Alt-F1 and use "sudo reboot", then hold shift to get the boot choices, boot into recovery mode with failsafe graphics, then uninstall the nVIDIA drivers and restart and everything is back to how it was before. If I then reinstall the nVIDIA drivers again the black screen appears; rinse and repeat. I've tried the GRUB-editing trick of replacing "splash quiet" with "nomodeset single" and this didn't seem to work.

I have also tried downloading the driver file from the nVIDIA website and, after spending a long time trying to work out how to get into runlevel 3, the installation first gives an error about a pre-install script being unable to run and then says that I have the Nouveau kernel which is not supported. I have no idea where to go from here.

Any help is much appreciated.

EDIT: Disregard, solved by chance. I installed a previous driver (which didn't work), then uninstalled and installed the newer driver, which happened to then work again. I checked the nVIDIA control panel and clicked "Save configuration" and a window popped up saying "Could not parse xorg.conf." I saved my new configuration over the previous xorg.conf file and it seems to have fixed the problem. I also made a backup. ;)

---

### Post by jao_madn on 2011-02-27
I think we have the same problem. Mine is nvidia geforce cuda 310M and the second laptop is 210M i have no luck trying to install both of them..the same procedure you did. 

I already scouch the internet and furom but no help..

My hope is that someday nvidia driver will work but not yet today..

Gud Luck..Hope you find a solution.

---

### Post by 3602 on 2011-02-27
This is what happens if you attempt to install nVIDIA's proprietary drivers on Optimus while running Linux.

---

### Post by Slave2Metal on 2011-02-27
Two separate issues, as his card is quite old and non optimus.  You'll have to use the integrated graphics until a fix comes along.
> **jao_madn said:**
> I think we have the same problem. Mine is nvidia geforce cuda 310M and the second laptop is 210M i have no luck trying to install both of them..the same procedure you did. 

I already scouch the internet and furom but no help..

My hope is that someday nvidia driver will work but not yet today..

Gud Luck..Hope you find a solution.

---

### Post by dinesh2n on 2011-03-25
Hi,
 Just wanted to share similar problem...may be useful for somebody
I had geforce 8400GS nvidia card (cuda enabled) fit in ubuntu 32 bit. When I restart computer it goes into black screen. CPU runs but no display. I installed cuda drivers and blocked all drivers others. Still the probelm of display was persisted. Later I formatted the system and did not used any cuda or nvidia drivers, I could not play games like qadrapassal and counter strike in wine. This time i enabled 3d accelerated driver of nVidea for ubuntu. Now I can play games and also the display problem is over.

Point is that if one uses cuda driver then graphic problem may come; because one has to block all other drivers. 


dinesh

---

