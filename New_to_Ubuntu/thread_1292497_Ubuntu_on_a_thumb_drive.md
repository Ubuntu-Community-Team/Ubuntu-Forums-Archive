---
title: "Ubuntu on a thumb drive"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Zero++ on 2009-10-15
I'm trying to install ubuntu on a thumb drive. I need to be able to install programs, do some OS customization, and save files on the thumb drive. I will also need to use this OS on multiple machines.  I've already read some posts on this and have ran into some problems. I have used the usb startup disk creator  (with the space for saves option) with no luck on saving changes. I have used unetbootin with no luck on saving changes when I restart. I have tried an install onto the drive but had trouble booting it. Maybe i did not get the boot loader in the correct spot? 
 
Any advice/help is greatly appreciated!

---

### Post by dominiquec on 2009-10-15
Are you able to boot into the USB system?  Did you allocate enough reserved space on the disk?  This is available from the USB Startup Disk creator tool.

---

### Post by DGortze380 on 2009-10-15
The machines BIOS must support booting from USB, or you must create a bootable CD that will allow you to boot the USB.

---

### Post by ibuclaw on 2009-10-15
The disk creator and unetbootin apps are designed only to turn a LiveCD into a LiveUSB, not a bootable USB operating system.

---

### Post by Zero++ on 2009-10-15
> **dominiquec said:**
> Are you able to boot into the USB system? Did you allocate enough reserved space on the disk? This is available from the USB Startup Disk creator tool.
 
I can into the USB system it just won't save changes. I have a 4 gig stick with over three gigs (remainder after OS install) of space reserved for storage.

---

### Post by sandyd on 2009-10-15
you probably need
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by dominiquec on 2009-10-16
From the USB Startup Disk Creator, did you enable the "Stored in reserved space option?"  In your USB disk, you should see a casper-rw file.

---

### Post by Zero++ on 2009-10-16
> **dominiquec said:**
> From the USB Startup Disk Creator, did you enable the "Stored in reserved space option?" In your USB disk, you should see a casper-rw file.
 
As stated I gave it 3 gigs of space!

---

### Post by dominiquec on 2009-10-16
> **Zero++ said:**
> As stated I gave it 3 gigs of space!

Oops, my bad. Do you have a casper-rw file on your USB disk?

---

### Post by beastrace91 on 2009-10-16
Why don't you just install Ubuntu directly to the thumb drive? It sounds like this will accomplish what you are looking to do. Boot from a LiveCD and when it comes to selecting the disc you wish to install to - select your thumb drive.

I have an 8gig setup this way - works great for saving my settings and Ubuntu is great about booting on different systems without complaints.

~Jeff

---

### Post by jmundinger on 2009-10-16
> **beastrace91 said:**
> Why don't you just install Ubuntu directly to the thumb drive? It sounds like this will accomplish what you are looking to do. Boot from a LiveCD and when it comes to selecting the disc you wish to install to - select your thumb drive.

I have an 8gig setup this way - works great for saving my settings and Ubuntu is great about booting on different systems without complaints.

~Jeff

What procedure did you use to do that.  I attempted to install Ubuntu 9.04 to a 4 gb thumb drive from the LiveCd running on a dual-boot Ubuntu/XP machine.  The result was a corrupted grub and something installed on the thumb drive that wouldn't boot.

---

### Post by Mighty_Joe on 2009-10-16
> **Zero++ said:**
> As stated I gave it 3 gigs of space!

There's a [Bug in the USB Creator]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544") (fixed for Karmic) that limits the size of the persistent casper-rw file to 2GB.  Either use a smaller size or download a larger file from pendrivelinux.com
If you do a full install to a USB drive, you have to make sure to install GRUB to the USB drive as well. There's some other things to optimize a USB drive install.  See my post [here]("http://ubuntuforums.org/showthread.php?t=1193680") for links to the procedure I use.

---

### Post by tarps87 on 2009-10-16
> **jmundinger said:**
> What procedure did you use to do that.  I attempted to install Ubuntu 9.04 to a 4 gb thumb drive from the LiveCd running on a dual-boot Ubuntu/XP machine.  The result was a corrupted grub and something installed on the thumb drive that wouldn't boot.

You need to tell the installer to install grub to the USB else it will write it to the hard drive, I can't remember where this option is but hopefully it will point you in the right direction

---

### Post by Mighty_Joe on 2009-10-16
> **tarps87 said:**
> I can't remember where this option is but hopefully it will point you in the right direction

It's the last step, after partitioning.  One is given a list of all the options you've chosen.  Under that list is an button marked "Advanced".  Clicking on it gives one the Grub options.

---

### Post by Carl Hamlin on 2009-10-16
Something important to think about when considering loading an operating system onto flash-based media: 

Flash supports a finite number of write/erase cycles before doing the big firework, and running a swap partition on a flash drive, or for that matter *any* disk-intensive operations *severely* shortens the length of the drive.

This may be a fun experiment, but I *really* wouldn't let any mission-critical data near this setup.

---

### Post by wlraider70 on 2009-10-16
There are ubs devices that are aware of this and will write equally to sectors. 
This doesn't solve the problem but it will slow it.

---

### Post by CaptainMark on 2009-10-16
ive had this grub problem before, i never knew what was causing it, good to know now though.

---

### Post by Mighty_Joe on 2009-10-16
> **Carl Hamlin said:**
> Flash supports a finite number of write/erase cycles before doing the big firework,

That finite number is pretty huge.  Like [90 million]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html") writes for a 1GB drive.  Thanks to wear-leveling, the larger the drive, the more writes one can expect.  Most flash drives will probably outlive their usefulness or go through the wash before failing because of excessive writes.
That said, when I run Ubuntu from a flash drive, I store everything I want to keep on a NAS.

---

### Post by CaptainMark on 2009-10-17
its good practice anyway to always keep back ups, tip: when you buy a flash drive. buy two and back up one to the other every week or so, its saved my bacon a few times

---

