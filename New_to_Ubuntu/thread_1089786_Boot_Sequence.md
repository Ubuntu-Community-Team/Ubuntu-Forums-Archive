---
title: "Boot Sequence"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by bj218 on 2009-03-07
On my system I have 2 HD'S 1 has WindowsXP the other 1 has Linux Mint 5 and Ubuntu 8.10 the boot sequence is Mint/WinXP/Ubuntu. How can I change this to have Ubuntu be the first to boot?
I am very new to the Linux OS so will need a lot of help.

---

### Post by Svensk023 on 2009-03-07
the easiest thing for you to do at the time being is to go to 
Applications > Add/Remove then search for a program called "Start-up Manager," this will allow you to select Ubuntu as the default OS to boot when you turn on your computer. If you would rather have the physical change of the order than thats an advanced step and we can go over that if my first suggestion dosent work out for you

---

### Post by bj218 on 2009-03-12
> **Svensk023 said:**
> the easiest thing for you to do at the time being is to go to 
Applications > Add/Remove then search for a program called "Start-up Manager," this will allow you to select Ubuntu as the default OS to boot when you turn on your computer. If you would rather have the physical change of the order than thats an advanced step and we can go over that if my first suggestion dosent work out for you

I downloaded and installed Startup Manager but that did not work. I think I have a problem with the Mint GRUB see the last entry of the Mint grub which is listed below.

## ## End Default Options ##          This is from Ubuntu

title		Ubuntu 8.10, kernel 2.6.27-7-generic 
root            (hd1,0) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic 
quiet 

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) 
root            (hd1,0) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro  single 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Ubuntu 8.10, kernel 2.6.24-19-generic 
root            (hd1,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic 
quiet 

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode) 
root            (hd1,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro  single 
initrd		/boot/initrd.img-2.6.24-19-generic 

title		Ubuntu 8.10, memtest86+ 
root            (hd1,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST

[## ## End Default Options ##   This is from Mint
[/COLOR]
title		Linux Mint, kernel 2.6.24-16-generic 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode) 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Linux Mint, kernel memtest86+ 
root		(hd1,3) 
kernel		/boot/memtest86+.bin 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Microsoft Windows XP Professional 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 



# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
# title		Linux Mint, kernel memtest86+ (on /dev/sdb1) 
# root		(hd1,0) 
# kernel		/boot/memtest86+.bin  
# savedefault 
# boot 

title Ubuntu Grub Menu                   
configfile (hd1,0)/boot/grub/menu.lst
   
In the BOOTUP Window highlighting UBUNTU and pressing ENTER does not start Ubuntu. You then have to Press ESC and ENTER to start Ubuntu

---

