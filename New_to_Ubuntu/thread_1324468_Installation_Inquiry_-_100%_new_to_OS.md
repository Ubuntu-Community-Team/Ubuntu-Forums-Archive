---
title: "Installation Inquiry - 100% new to OS"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by at0msk on 2009-11-12
I have a laptop without a CD-ROM drive. It's an older one to so there is no support in the BIOS for booting from a USB device.

I have an enclosure with a USB-to-IDE interface and can hook the laptop's HDD to it and then to a Windows system. I used this method to install XP on the laptop. Through a command line I came across I was able to copy the needed Windows setup files to the drive and after inserting the drive into the laptop I was able to boot into Windows setup and go from there.

Can this be done with Ubuntu? I know that Wubi can install Ubuntu from Windows but the drive is only a 20GB drive and I'd rather not dual boot. I'd prefer a clean install.

Any Guru's here with some nifty tips/tricks? I'm an avid fan of BitTorrent and ISO's in general. I use MagicISO and ImgBurn for most of my projects. I'm not afraid of extracting an ISO and dissecting it's parts...

---

### Post by hwttdz on 2009-11-12
Two things I could think of would one be putting the drive in another machine and installing ubuntu to the drive then moving it.  Or copying the disk image to a partition on the disk then installing ubuntu from a "cd" on the hard disk to a different partition on the hard disk.  Then finally removing the partition on which you put the cd image.  Sounds like a tricky task.  Though you might not be able to mount a hard disk as a "cd" without an operating system.

---

### Post by CaptainMark on 2009-11-12
if the laptop is so old it has no cd drive i would be put off using ubuntu, it probaly has very little memory so you might find xubuntu, dsl or puppy llinux work better.

---

### Post by at0msk on 2009-11-12
> **CaptainMark said:**
> if the laptop is so old it has no cd drive i would be put off using ubuntu, it probaly has very little memory so you might find xubuntu, dsl or puppy llinux work better.


Well it's without one because it died. :-P The laptop has 684MB of RAM, 1GB max capacity.

---

### Post by oldfred on 2009-11-12
Do you have a floppy to use to boot? If so you can create a boot floppy and then use that to boot your USB device.

[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)
You can use supergrub to create disks
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.justlinux.com/forum/showthread.php?t=142409](http://www.justlinux.com/forum/showthread.php?t=142409)

You just about have to boot from the usb device so you can repartition/reformat the hard drive on your portable. Once that is done any mimimal install like a network install or copy an iso to a small partition with just mimimul boot will get you started.

---

### Post by at0msk on 2009-11-12
> **hwttdz said:**
> Two things I could think of would one be putting the drive in another machine and installing ubuntu to the drive then moving it.


I thought about this but knowing only Windows for the span of my IT life I would fear hardware issues. Would Ubuntu care that the board and processor available during install changed?

> **hwttdz said:**
> 
 Or copying the disk image to a partition on the disk then installing ubuntu from a "cd" on the hard disk to a different partition on the hard disk.  Then finally removing the partition on which you put the cd image.  Sounds like a tricky task.  Though you might not be able to mount a hard disk as a "cd" without an operating system.

This does sound tricky but I've seen the recommendation else where so I may look further into this...

> **oldfred said:**
> Do you have a floppy to use to boot? If so you can create a boot floppy and then use that to boot your USB device.

[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)
You can use supergrub to create disks
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.justlinux.com/forum/showthread.php?t=142409](http://www.justlinux.com/forum/showthread.php?t=142409)

You just about have to boot from the usb device so you can repartition/reformat the hard drive on your portable. Once that is done any mimimal install like a network install or copy an iso to a small partition with just mimimul boot will get you started.

Unfortunately there is no floppy drive either. :\ I can take the drive out of it though! :D

---

### Post by Tahakki on 2009-11-12
I use a bootloader on a floppy called PLoP, as I can't boot usb drives and my computer refuses to boot any CD with GNOME.

---

### Post by at0msk on 2009-11-12
> **Tahakki said:**
> I use a bootloader on a floppy called PLoP, as I can't boot usb drives and my computer refuses to boot any CD with GNOME.

I tried installing PLoP on the laptop, which has Windows 7 installed on it (because I could, that's why!) but plpbtldr.bin is "missing or corrupt." So I can't boot to it. :( 

I can drop $45 on a DVD ROM for the laptop. Just wanted to explore alternatives before spending money on the laptop since it's basically a sandbox.

---

### Post by at0msk on 2009-11-12
> **hwttdz said:**
> Two things I could think of would one be putting the drive in another machine and installing ubuntu to the drive then moving it.  Or copying the disk image to a partition on the disk then installing ubuntu from a "cd" on the hard disk to a different partition on the hard disk.  Then finally removing the partition on which you put the cd image.  Sounds like a tricky task.  Though you might not be able to mount a hard disk as a "cd" without an operating system.


Bah, I was thinking that maybe I would create a partition and install Ubuntu to it but if I were able to delete the Windows partition I don't think I would be able to regain that space (meaning combining them so there's only one partition rather than 10GB for the OS and 10GB for random stuffs)... On that note how is disk management in Ubuntu?

OR Could I just install Ubuntu to the same partition Windows is on then delete the Windows folder from Ubuntu or would I be facing write access issues?

---

