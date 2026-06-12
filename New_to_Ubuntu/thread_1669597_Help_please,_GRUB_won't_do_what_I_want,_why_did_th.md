---
title: "Help please, GRUB won't do what I want, why did they go and change it?"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Zralou on 2011-01-17
Not been here for a while, and now i'm back with the same problem I had last time I was here.

To simplify things, i've installed 10.10 and want to use the WinXP boot loader to dual boot Win + Linux.  When I first installed Ubuntu 2 years ago I spend several days searching for a way to do this, and finally found the answer.
However, now I find GRUB has changed and I can no longer use the same solution I did 2 years ago (which was to install GRUB to a floppy).

Currently, I have WinXP installed on the first HDD, and ubuntu installed on a second HDD.  During the linux install it installed GRUB to the MBR (no option to install to FDD) so I 'FixMBR' using XP disk.  Now I have ubuntu installed, but no way to load it.

Is there a way to use the new version of GRUB without loosing my XP bootloader, or can the old version of GRUB be used with 10.10, and if so, how?.

Thanks
Sara Lou

---

### Post by bodhi.zazen on 2011-01-17
Not that I know of.

I would suggest you either use grub2 (rather then the windows boot loader) or perhaps ask on a windows forum.

---

### Post by oldfred on 2011-01-18
I have not tried it but Herman has some info:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc)

Is this an older computer that you cannot in BIOS choose to boot the second hard drive? Or you can only boot the IDE primary master as set with the jumpers on the hard drive or by where it is located on the cable (cable select).

Grub2 does work well and will let you boot either Ubuntu or windows. If you want to revert to directly booting windows you can easily reinstall a windows boot loader from the XP disk or install lilo which works just like the windows boot loader in the MBR.

---

### Post by oldfred on 2011-01-18
I have not tried it but Herman has some info:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc)

Is  this an older computer that you cannot in BIOS choose to boot the  second hard drive? Or you can only boot the IDE primary master as set  with the jumpers on the hard drive or by where it is located on the  cable (cable select).

Grub2 does work well and will let you boot  either Ubuntu or windows. If you want to revert to directly booting  windows you can easily reinstall a windows boot loader from the XP disk  or install lilo which works just like the windows boot loader in the  MBR.

You can also uninstall grub2 and use grub if it works for you.

---

### Post by Zralou on 2011-01-18
Hi, thanks for the replies guys.

This is a modern PC, and I can choose which hard drive to boot in BIOS, but that's not what I wanted.
I know GRUB is more than capable of doing what I need, but I wanted to use XP's bootloader, I already have it setup as my boot manager and have XP and 8.4 Hardy booting from it happily.

When I first installed Hardy 2 years ago everyone told me I couldn't use NTDLR, but I spent several day's searching the internet till I eventually found a solution that worked.
Now, 2 years on, I wanted to try a newer version and I end up with the exact same problem I had first time round!!.  It doesn't give much incentive to move away from Windows if you have to completely relearn everything everytime you upgrade.

Is it possible to use GRUB legacy with 10.10?, I know that works.

Sara Lou

---

### Post by Quackers on 2011-01-18
Why not use the grub menu, then edit it so that Windows is the default option?
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Zralou on 2011-03-01
Well after some research it seems it is possible to dump GRUB2 and replace it with GRUB legacy, which will allow me to do what I wanted with Linux.

apt-get remove grub-pc
apt-get install grub

Sara Lou

---

