---
title: "Checking All Major Hardware Works"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Tayl on 2011-02-08
Good morning all.

Basically, I'm in the process of testing the latest LiveCD to make sure that everything works before doing the initial install. To my surprise, everything does seem to work (it's never normally that smooth for me with anything). However, while I know I can do everything in terms of what I can on a Windows machine (see the desktop - video/graphics related, move the mouse and what not) how do I actually go about checking that the hardware is installed and running correctly?

While I know I have a desktop environment to maneuver around within but that doesn't necessarily mean that the graphics drivers are installed and working corre
ctly does it.

Running this on my laptop at the moment. Specs:

Chipset: Intel HM55 Express Chipset
Processor Name: Intel Core i3-330M Processor
Memory Size (GB): 4
Memory Specification: PC3-8500
Memory Type: DDR3 SDRAM
Memory Speed (MHz): 1066
Hard Drive Type: Serial ATA
Hard Drive Capacity (GB): 500
Hard Drive Speed (rpm): 5400
Optical Drive Type: DVD+-RW/+-R DL/RAM
Resolution: 1366 x 768
Aspect ratio: 16:9
Max Resolution External Display: 2048 x 1536
Graphics Card Name: ATI Mobility Radeon HD 5470 Graphics
Video RAM memory (MB): 512

Are there any simple commands / ways to check that everything is working fine and drivers are installed correctly / functioning as expected? This is using the latest Ubuntu release.

Regards,

Tayl.

---

### Post by beew on 2011-02-08
Install Ubuntu in an external hard disk (not a live usb with persistence, but a full installation into an external hard disk) and then use it to test the hardware by booting into it. The reason for a full install is that you can install propietary graphic driver if needed, update kernel and mess around and trouble shoot in whatever way you would in a real install (because it is a real install!)whereas live usb doesn't support that kind of changes.

To install into an external hard drive. 

First create a live cd/live usb. Boot into it, then connect the external hard drive you want to install Ubuntu into and then just go through the installation like you would normally, except when prompted, choose "manual install" and make sure that you are installing into the external drive instead of the internal one (you can see the layout in the partition manager during the installation, it may have name like /dev/sdb or /dev/sdc (/dev/sda is usually your internal hard drive, don't install over it or you will wipe out the existing OS, /dev/sdb maybe the live usb you are using to do the installation) 

Also, you have to install the bootloader in the correct drive (say /dev/sdc)  In  10.04 you do this by choosing "advanced" and set the target for the bootloader in the last step. I think in 10.10 you choose that when you are presented with the partition manager (choose manual install, remember)

Now some people would remove the internal drive first to be ultra safe, you can do it as well (though I never did, too much trouble for me :))

---

