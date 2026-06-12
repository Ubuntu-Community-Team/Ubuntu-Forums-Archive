---
title: "Install to USB"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by cfree220 on 2009-01-09
I was wondering if it is possible to install Ubuntu to a USB drive. I know how to make a live USB, but I'd rather have it behave as though it were installed to the thumb drive.

---

### Post by Captain_tux on 2009-01-09
Ask and you shall receive!

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

If you're using Intrepid, click on **System > Administration > Create a USB startup disk**.

---

### Post by evilkastel on 2009-01-09
Thats pretty much a liveUSB. There is no way to do a "regular" ubuntu install in a USB pendrive since the USB pendrive has no hardware associated. In pendrivelinux they sell LiveUSBs that have persistent files, but still is not a ubuntu install, is a liveUSB.

---

### Post by djbushido on 2009-01-09
Okay, technically yes, this is possible.
HOWEVER!!!: it is highly recommended against because of read/write speeds, and IT WILL KILL YOUR FLASH DRIVE because of the nearly incessant read/write cycles.

If you decide to go through with it, when you install Ubuntu, there should be a listing for connected usb devices. To make sure grub gets installed to just the usb device, i recommend unplugging any hard drives you might have.

Again, you have been warned. Try booting the install cd, then check and make sure you can't install to a flash drive.

By the way, you probably need about a 4-8 gb flash drive to hold Ubuntu. I have installed my (X)ubuntu to a usb hard drive, so your usb disk should work.

---

### Post by cfree220 on 2009-01-29
Hmmm.... I'm going to come back to this thread for a second....
djbushido, does the size of the OS have an impact on whether or not you will be able to boot from flash? I tried installing (as opposed to creating liveUSB) on a 4 gig, but it could never get past GRUB.

---

### Post by snowpine on 2009-01-29
A lot of misinformation in this thread!

You can indeed do a "full" install of Ubuntu to any flash device (USB thumb drive, SD card, etc). Once Ubuntu is booted, it doesn't know or care what kind of drive it's running from.

You will need a 4gb minimum drive. Boot from the Live CD, run the installer, and install to your USB drive just as you would to any other hard drive. When you get to Step 7, click Advanced Options and install the Grub bootloader on the correct device (the USB drive).

It is true that your drive will wear out eventually, but who cares about whether a $10 flash drive wears out in 1 year instead of 2 years? There are numerous well-documented hacks to reduce wear on the drive, such as using ext2 filesystem, not using swap, mounting /tmp to ram, etc. Check out forum.eeeuser.com for more info; the eee pc's use flash-based SSD drives, so the tips & tricks you'll find over there also apply to a USB flash device.

Hope that clears up some of the misconceptions. :)

---

### Post by djbushido on 2009-01-29
What misconceptions? Those are tricks to extend life, not any misinformation. Let's make that clear up front. Please.

Anyway, the size of the OS doesn't matter, as long as there is somewhere to boot. What does matter is that some BIOS's don't support drives over 356 GiB. I think. Somewhere around there.

Point is, don't worry about flash drive size. If you could post output of
```
cat /path/to/flash_drive/boot/grub/menu.lst
cat /path/to/flash_drive/boot/grub/grub.conf
ls /dev/disk/by-uuid -lha
```
Along with any GRUB error messages, that would be appreciated. A problem I had recently was that GRUB wasn't actually in my MBR. Anyway, post the results of those commands, as this will help diagnose some problems. Thanks.

---

### Post by snowpine on 2009-01-29
Hi DJBushido, no offense meant, you offer some good advice. :)

I was specifically responding to the statements: "There is no way to do a 'regular' ubuntu install in a USB pendrive" and "IT WILL KILL YOUR FLASH DRIVE." 

I frequently boot from flash drives. Not only is it not impossible, I have never, ever lost any data or had a flash drive die. Flash drives are a common and inexpensive storage device; it would be silly to put them in a vault and never use them for fear of wearing them out. ;) If flash storage is incabable of withstanding the rigors of a Linux OS, why is it  used in so many netbooks like the eee pc?

It is true that flash storage varies in quality. Some of the earlier devices were very limited in write cycles, but the newer drives on the market are designed to last for 10 years or more even under constant use...

---

### Post by cfree220 on 2009-01-29
I'm not sure where I'm supposed to be entering
```

cat /path/to/flash_drive/boot/grub/menu.lst
cat /path/to/flash_drive/boot/grub/grub.conf
ls /dev/disk/by-uuid -lha

```
I run Windows as my primary OS and use Linux primarily for things like personal file servers. I'd like to have a portable OS so that I know that I'm not going to run into any virus problems when using school computers (and, of course, for times when the only thing that stands between you and Ubuntuforums.org is a stupid Windows password). My only current Linux box is 8.10 server sans GUI.... so I don't really have a desktop environment to run any commands from...

I think I'm probably misunderstanding what you're saying I should do. Can I enter code when it gets stuck at GRUB?

---

### Post by crjackson on 2009-01-29
misinformation
&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;
**evilkastel**
> **There is no way to do a "regular" ubuntu install in a USB pendrive **since the USB pendrive has no hardware associated. In pendrivelinux they sell LiveUSBs that have persistent files, but still is not a ubuntu install, is a liveUSB. 


[SIZE="5"]Correct![/SIZE]
&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;
**snowpine**
> A lot of misinformation in this thread!

You can indeed do a "full" install of Ubuntu to any flash device (USB thumb drive, SD card, etc). Once Ubuntu is booted, it doesn't know or care what kind of drive it's running from.

You will need a 4gb minimum drive. Boot from the Live CD, run the installer, and install to your USB drive just as you would to any other hard drive. When you get to Step 7, click Advanced Options and install the Grub bootloader on the correct device (the USB drive).

It is true that your drive will wear out eventually, but who cares about whether a $10 flash drive wears out in 1 year instead of 2 years? There are numerous well-documented hacks to reduce wear on the drive, such as using ext2 filesystem, not using swap, mounting /tmp to ram, etc. Check out forum.eeeuser.com for more info; the eee pc's use flash-based SSD drives, so the tips & tricks you'll find over there also apply to a USB flash device.



same for me too...
&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;&#8595;
**snowpine**
> I frequently boot from flash drives. Not only is it not impossible, I have never, ever lost any data or had a flash drive die. Flash drives are a common and inexpensive storage device; it would be silly to put them in a vault and never use them for fear of wearing them out.  If flash storage is incabable of withstanding the rigors of a Linux OS, why is it used in so many netbooks like the eee pc?

It is true that flash storage varies in quality. Some of the earlier devices were very limited in write cycles, but the newer drives on the market are designed to last for 10 years or more even under constant use...

---

### Post by djbushido on 2009-01-29
True, and I haven't had a flash drive go on me yet. However, my hard drive is on the way out, and I have had to check the disk every time I boot up. No, it is possible to install a full OS to a drive, but there is not much of a benefit over persistent for flash drives. I just don't trust my drive to an OS, because I usually have very important school stuff on it.

So in the end, it is possible, but I would recommend a persistent setup unless you really needed the full-blown OS, or had a need otherwise, because you will save a lot of space, and save life in your drive.

BTW snowpine - are new drives really manufactured to those standards? 'Cause if so, some people at Sandisk have some talkin to do... And please don't call anything misinformation unless it is _actually_ wrong. You can say you have a better idea, but IMO, that was a bit rude.

EDIT: Sorry, more information forthcoming while writing.
The commands should be run from the livecd, or from a linux install. If you can use "ls" in windows, let me know.

EDITEDIT: If you can run these from grub, definitely let me know. you have problems.

Anyway, what problems still exist? I'm not sure what is left to do.

---

