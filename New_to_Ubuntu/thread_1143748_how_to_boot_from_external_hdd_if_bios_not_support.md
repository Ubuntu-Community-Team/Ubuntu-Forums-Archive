---
title: "how to boot from external hdd if bios not support??"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by stinger30au on 2009-04-30
i have installed ubuntu 9.04 to an external usb hdd. i have tried it on a few pc's i can set the bios to "boot from usb hdd"
 
i have a toshiba satellite a60 that id like to get it to boot ubuntu from the hdd
 
the bios does not support usb booting
 
is there a cd or floppy  i can make or download to enable this to happen?
 
thanks

---

### Post by Judgegeo on 2009-04-30
> **stinger30au said:**
> i have installed ubuntu 9.04 to an external usb hdd. i have tried it on a few pc's i can set the bios to "boot from usb hdd"
 
i have a toshiba satellite a60 that id like to get it to boot ubuntu from the hdd
 
the bios does not support usb booting
 
is there a cd or floppy  i can make or download to enable this to happen?
 
thanks

Youll need to update your BIOS by flashing it with the latest version. They might have added USB support, but then again they might not have.

---

### Post by halitech on 2009-04-30
Is windows installed on the internal drive? If so then you could edit the windows boot loader to list Ubuntu on the external and allow you to boot it. If you don't want to do that then a boot disk is possible but not sure where you would get one.

---

### Post by stinger30au on 2009-04-30
> **Judgegeo said:**
> Youll need to update your BIOS by flashing it with the latest version. They might have added USB support, but then again they might not have.


done this just now. no usb boot :-((

---

### Post by stinger30au on 2009-04-30
> **halitech said:**
> Is windows installed on the internal drive? If so then you could edit the windows boot loader to list Ubuntu on the external and allow you to boot it. 


im happy to do this

how do i do it?

---

### Post by halitech on 2009-04-30
I'm not completely sure. Is it Windows 2000, XP or Vista?

---

### Post by stinger30au on 2009-04-30
windows xp home


i have been for a hunt with google and found this

[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

i have 9.04.
will investiage further tomorrow afternoon after work. im going to catch some zzzz's for the night

---

### Post by halitech on 2009-04-30
that should work, just replace 8.10 in the menu list with 9.04 and use the 9.04 cd to create the cd.

---

### Post by lisati on 2009-04-30
There's also [Smart Boot Manager]("http://sourceforge.net/projects/btmgr/"), which can be put on a floppy to let you choose where to boot your main OS from.

---

### Post by stinger30au on 2009-04-30
thanks guys

i will put it to the test tonight

---

### Post by logos34 on 2009-04-30
smartbootmanager doesn't have usb support, and how could the windows method work when your Bios does not support usb boot (can't see the ext drive)?

I think the only way is to put the kernel on the internal disk and boot it from there:
[https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20an%20internal%20hard%20drive](https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20an%20internal%20hard%20drive)

---

### Post by stinger30au on 2009-04-30
i followed these instruction

[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

copied here just incase the other web site vanishes

==========================================
This ***USB Boot CD*** can be used to boot a Ubuntu 8.10[COLOR=#009900][FONT=&quot]_USB flash drive_[/FONT][/COLOR] on computers with a BIOS that does not natively support booting from USB. The [COLOR=#009900][FONT=&quot]_boot CD_[/FONT][/COLOR] contains a grub bootloader that loads the initrd and vmlinuz kernel from the CD and then proceeds to locate the filesystem on the USB flash drive. Because the USB drivers are preloaded from the initrd on the CD, the USB flash drive can then easily be detected.
 
 Could also be used to *Boot Ubuntu from a USB Flash Drive on Apple Mac, Macbook and, Macbook Pro*.
 [COLOR=#800000]**Note:**[/COLOR] This USB Boot CD should work on most older systems. However, it has been noted from testers that some systems with hardware that only supports USB 1.0 may not work.
 Can be used to boot flash drives created using the [USB Ubuntu 8.10 tutorial]("http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/")
 **USB Boot CD for Ubuntu 8.10 creation essentials**
 
[LIST]
[*][COLOR=#0066FF]PC with a BIOS that does not support booting from USB[/COLOR]
[*][COLOR=#0066FF]Working CD Drive and USB Port[/COLOR]
[*][COLOR=#0066FF]Ubuntu 8.10 Live CD[/COLOR]
[*][COLOR=#0066FF]USB flash drive with Ubuntu 8.10 preinstalled[/COLOR]
[/LIST]
 **How to Create a CD to Boot Ubuntu from USB**

 The following process will enable you to create a Boot CD that can be used to Boot Ubuntu 8.10 from a USB Flash drive on systems that do not natively support booting from USB.
 
[LIST=1]
[*]Insert the **Ubuntu 8.10 Live CD** and restart your computer, booting from the CD
[*]Open a Terminal and type **mkdir -p ubcd/boot/grub**
[*]Type **cp /usr/lib/grub/i386-pc/stage2_eltorito ubcd/boot/grub**
[*]Type **gedit ubcd/boot/grub/menu.lst**
[*]Add the following information to your menu.lst file and save it to ubcd/boot/grub
[INDENT]title Run Ubuntu 8.10 from USB DISK
root (cd)
kernel /boot/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent quiet splash
initrd /boot/initrd.gz
boot
[/INDENT]
[*]Type **cp /cdrom/casper/initrd.gz ~/ubcd/boot**
[*]Type **cp /cdrom/casper/vmlinuz ~/ubcd/boot**
[*]Type **mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o usbcd.iso ubcd**
[*]Burn the **usbcd.iso** to a CD
[/LIST]
 **Booting from the USB Boot CD**

 
 
[LIST=1]
[*]Shutdown your computer
[*]Insert both the Boot CD and  the Ubuntu 8.10 USB flash drive
[*]Set your BIOS or Startup Menu to boot from CD
[*]Start your computer (booting from the  CD)
[/LIST]
 If all goes well, the CD should load the necessary USB drivers, detect  your
USB device and proceed to boot Ubuntu 8.10 from the flash drive.
==========================================

i burnt the cd
it starts up and says it will boot ubuntu 9.04 usb
up comes the ubuntu splash screen and the knight rider led waves backwards and forwards for a few minutes and i can see the usb hdd light flashing away as it loads

then i get a "busybox v1.10.2" screen pop up

under that i get this

(initramfs)

and next to that is a flashing cursor, so it almost worked!

---

### Post by logos34 on 2009-04-30
> **stinger30au said:**
> 

yep, that's the other way--put the kernel on a boot cd.

---

### Post by stinger30au on 2009-05-01
> **logos34 said:**
> yep, that's the other way--put the kernel on a boot cd.


did that, and it almost worked

i burnt the cd
it starts up and says it will boot ubuntu 9.04 usb
up comes the ubuntu splash screen and the knight rider led waves backwards and forwards for a few minutes and i can see the usb hdd light flashing away as it loads

then i get a "busybox v1.10.2" screen pop up

under that i get this

(initramfs)

and next to that is a flashing cursor, so it almost worked!

any ideas how to fix this?

---

### Post by logos34 on 2009-05-01
maybe it's a [bug]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/363038")

---

### Post by stinger30au on 2009-05-01
> **logos34 said:**
> maybe it's a [bug]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/363038")

ah ha... reading this it looks like it afftects the r/s and thats what i have

looks like i need to download the final as the bug is solved...

must try this

---

### Post by stinger30au on 2009-05-02
i gave up on this and decided to dual boot the laptop instead

it has a 30 gig hdd so  have given 6 gig to ubuntu 9.04

i think from what i have been reading the reason why my boot cd failed is becase the external hdd i have setup i made it boot on a pc that had a bios to allow it to boot and let it to its updates

when i made the boot cd i went to the laptop and put the original 9.04 boot dc in with the usb hdd plugged in and made the boot cd

from what i gather, the kernel on the boot cd mus be the *SAME* as the kernel on the external hdd

cos i did the update on the usb hdd and it updated the kernal so it was newer then the one on the cd, i think this is the reason for the failure

no matter now... it works and i will just save my data to the 160 gig external hdd i have

i must have another go thu at making a boot cd as i have a friend who has a toshiba and his hdd controller on his laptop mobo has died and im sure we can keep it going if we use an external hdd and a boot cd.
the latop is 4 year old so its warranty is over

---

### Post by logos34 on 2009-05-02
> **stinger30au said:**
> 
i think from what i have been reading the reason why my boot cd failed is becase the external hdd i have setup i made it boot on a pc that had a bios to allow it to boot and let it to its updates


you mean you just downloaded the updates or did you also install ubuntu to the usb on another machine?  If the latter, that could be the explanation for your troubles. 

I don't think the difference in the kernels is the issue--you'll just be running the older one from the cd.  Should work all the same.  I boot my previous kernel every once in a while.  

What about booting the kernel for the usb installation from the *hard disk*, as I suggested above? Might not work, but worth a try--you already have an ubuntu partition on it.  If successful, you can then reduce the 6 gb / to just the bare minimum to hold the kernel (~50 mb).  Then you can have the whole 30 gb for windows, and linux segregated on the external.

---

### Post by stinger30au on 2009-05-03
> **logos34 said:**
> you mean you just downloaded the updates or did you also install ubuntu to the usb on another machine?  If the latter, that could be the explanation for your troubles. 

I don't think the difference in the kernels is the issue--you'll just be running the older one from the cd.  Should work all the same.  I boot my previous kernel every once in a while.  

What about booting the kernel for the usb installation from the *hard disk*, as I suggested above? Might not work, but worth a try--you already have an ubuntu partition on it.  If successful, you can then reduce the 6 gb / to just the bare minimum to hold the kernel (~50 mb).  Then you can have the whole 30 gb for windows, and linux segregated on the external.


i understand what your talking about, but how to actually *DO* what your talking about i have no idea

---

### Post by logos34 on 2009-05-03
> **stinger30au said:**
> i understand what your talking about, but how to actually *DO* what your talking about i have no idea

It's all explained in the link in Post #11.

---

### Post by stinger30au on 2009-05-03
> **logos34 said:**
> It's all explained in the link in Post #11.

awesome. thanks

---

