---
title: "Ubuntu Installation Error"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by Maese909 on 2011-08-26
Hey all. I have just downloaded the Ubuntu 11.04 Iso file and have put it on my 4GB SanDisk flash drive. I am now trying to boot from my flash drive so I can install Ubuntu, but after setting the USB drive to be the first boot option and booting thereafter, I get the error that is on this site:
[[COLOR=#22229c]http://www.pendrivelinux.com/error-c...l-image-linux/[/COLOR]]("http://www.pendrivelinux.com/error-c...l-image-linux/") 
 
Any help is appreciated as this is my first time trying out Linux!:P
 
P.S. I have the syslinux.cfg and txt.cfg files in the flash drive. Also here are the contents of syslinux.cfg:
 
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
 
... and here are the contents of txt.cfg:
 
default live
label live
menu label ^Run Ubuntu from this USB
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash --
label live-install
menu label ^Install Ubuntu on a Hard Disk
kernel /casper/vmlinuz
append cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz splash --
label memtest
menu label Test ^memory
kernel /install/mt86plus
label hd
menu label ^Boot from first hard disk
localboot 0x80

---

### Post by flurospar on 2011-08-26
What software are you using to do this? Unetbootin?

Moreover, can you boot the pen drive to run Ubuntu in another computer?

Please repost the link, this one does not work!

---

### Post by Maese909 on 2011-08-26
I used the universal USB installer to get the iso file containing Ubuntu onto my flash drive. Here is the site again where it describes the exact problem I have:
[[COLOR=#22229c]http://www.pendrivelinux.com/error-c...l-image-linux/[/COLOR]]("http://www.pendrivelinux.com/error-c...l-image-linux/") 

When I boot from the flash drive, it says:
Could not find kernel image: vesamenu.c32
 
This error occurs both on my desktop and laptop. Thanks a ton for any help!

---

### Post by ratin3 on 2011-09-09
> **Maese909 said:**
> I used the universal USB installer to get the iso file containing Ubuntu onto my flash drive. Here is the site again where it describes the exact problem I have:
[[COLOR=#22229c]http://www.pendrivelinux.com/error-c...l-image-linux/[/COLOR]]("http://www.pendrivelinux.com/error-c...l-image-linux/") 

When I boot from the flash drive, it says:
Could not find kernel image: vesamenu.c32
 
This error occurs both on my desktop and laptop. Thanks a ton for any help!

You have to make sure vesamenu.c32 file is there inside syslinux folder of live cd. Its a cpio archive of graphical menu.

---

### Post by sandyd on 2011-09-09
just use unetbootin. works perfectly without any fuss.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

