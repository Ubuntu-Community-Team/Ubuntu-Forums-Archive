---
title: "How to get full use from SD drive?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by pilot4pay on 2009-11-29
Someone tell me if I'm mistaken about these observations:
1. a bootable USB or SD need not be larger than 1Gb because the system only sees the 7xx Mb of the boot image
2. changes or updates are not saved no matter how large the device, because of the above.

What I would like to be able to do is make a truly bootable SD, IE changes and updates are saved to the drive. 

Is there another way to create a bootable SD or flash that is used like a normal hard drive installation?

Lastly, if I boot from a CD image and select install, will it automaticly install to the C: drive without further prompting, and or will I have a chance to either abort or point the installation to another device?

---

### Post by sgosnell on 2009-11-29
You can install to an SD card, but you need two drives to do it.  You start with the live CD (or USB drive), and use that to install to an SD or USB drive, or to your HDD/SDD.  The initial drive need not be bigger than 1GB because the .iso isn't that big, and fits on a standard CD.  You'll need a couple of GB for a full install, though, maybe more, depending on how much you want to add.

When you do the install, it will let you select the drive you install to.  Nothing is automatic, and you can back out right up to the final click on 'Forward'.  Your HDD is /dev/sda (the partitions on it will be sda1, sda2, etc, if there are more than one, and sda1 will always be the first partition).  Your SD/USB drives will be sdb1, sdc1, etc, depending on how many and in which order they were mounted.  You should be able to tell which is which by the size and perhaps the volume ID.  Boot from the drive to which you burned the .iso, and then install to another drive.  If you already have it on an SD card, and want to install to SD card, you're going to have problems, because you can't install to the drive you're installing from.  Burn the .iso to a small USB drive, boot from it, and then install to a large SD card.  You can certainly use a card reader as the other drive, and install to an SD card in the reader, or reverse it and boot from the SD card in the reader, and install to a card in the slot on your computer.  It makes no difference which way you go.

And again, you can back out right up to the end.  On screen 7, just before the final click to install, I suggest clicking on the Advanced button and selecting the SD card as the place to put the boot loader, don't put it on sda1.  If you do, you won't be able to boot from the HDD unless the SD card is in the slot.  With the boot loader on the SD card, you can press Esc at the BIOS screen at boot, and select the drive you want to boot from, without affecting the HDD at all.

---

### Post by pilot4pay on 2009-11-29
Thnaks a bunch, I think that's the info I was trying to find out. I really want to get linux up and running, Just I'm pretty ignorant about all the details and tricks. :p

---

### Post by jrrader on 2009-11-29
I install from the Live CD to USB sticks all the time.  Just run it like a normal install except point it to your card/usb when you're at the partition selection screen.  On the last page before install, when it gives you the page to review what is about to happen, click advanced to make sure your boot loader is going to the memory stick rather than your hard drive.

I did this last weekend for my brother-in-law when he could no longer get into windows but I also have one that I use (when I'm away from home but need to do homework, or when I need to fix someone's computer - really comes in handy.)

---

### Post by pilot4pay on 2009-11-29
Update. I booted my tower system with the netbook remix CD. I plugged in the SD card, and the file system window opened showing the 16Gb card. I then opened th install netbook remix from the favorites tab. When it got to the partition selection screen, the SD was not available as a selection.
What am I missing?

---

### Post by sgosnell on 2009-11-29
I don't use the netbook remix, I don't like it, and straight vanilla Ubuntu works better for me.  But the install should work pretty much the same, and the SD card should be there, but it won't have the same name.  It will be listed as sdb1, sdc1, or something like that, depending on how many drives you have.  You should be able to recognize it by the size.

---

### Post by pilot4pay on 2009-11-29
> **sgosnell said:**
> I don't use the netbook remix, I don't like it, and straight vanilla Ubuntu works better for me. But the install should work pretty much the same, and the SD card should be there, but it won't have the same name. It will be listed as sdb1, sdc1, or something like that, depending on how many drives you have. You should be able to recognize it by the size.
 
Yes, right. I should be able to recognise it by the size. There were no  16Gb drives, I can also count, and all I saw were the three hard drives I have, two 500Gb and a 1Tb drive that are installed.
I shouldn't think it would matter which version I was trying to install, but I guess anything is possible, I know little to nothing about this OS.
Thanks for trying.

---

### Post by sgosnell on 2009-11-30
Did you have the SD card installed before booting from the CD?  You need to have it in place before booting, not after.  If it still doesn't show up, I'm stumped.

---

### Post by efflandt on 2009-11-30
If you are trying to install to SD, what is the SD plugged into?  For example my laptop has an SD slot, but it does not show up as a regular /dev/sd..., instead it shows up as /dev/mmcblk0 with partition /dev/mmcblk0p1.  So the USB Startup Disk Creator does not work with that, and not sure about a regular install.  It does automount and gnome shows an SD icon for it.  But my laptop will not boot from it even if it has a bootable system on it.

If I put the same SD (actually microSD in SD adapter) in a USB card reader, USB Startup Disk Creator works, and I can boot from it.  I put live/install 9.10 64-bit on 2 GB microSD just to see how it works.  It is slightly slower than regular USB stick, but much faster than Sandisk Cruzer with U3 (U3 firmware mounts as additional sr device).

The built-in card reader on my disktop is USB, so booting from SD works there.

8 GB is minimum recommended for a full system.  4 GB will work, but at about 2.5 GB installed with just updates and audio/visual packages, you could run tight on space quickly, especially if you need a swapfile.  Note that near end of full install remember to use **Advanced** button **put grub on USB mbr**, instead of default to your main hard drive.  Also use tmpfs for /tmp in fstab to minimize frequent disk writes for non-persistant data (which live iso on CD or USB does):

tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by jacobs444 on 2009-11-30
is your bios set to initialize usb on boot?

---

