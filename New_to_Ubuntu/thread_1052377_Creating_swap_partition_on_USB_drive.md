---
title: "Creating swap partition on USB drive"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by ubername on 2009-01-27
Hi

I have been trying to create a bootable USB drive (note: I don't want a bootable startup USB to install *buntu on another machine, I want a USB drive  which will actually boot into *buntu on a machine where the boot settings allow boot from USB). I have followed a variety of tutorials, but it seems to me that my major problem has been that when I boot from the live CD and try to install to the USB stick it all seems to work until the part where the swap partition is created   (using guided partition management from the CD), at which point I get an error message along the lines of 'partition #5 error creating swap partition'. Any Clues? TIA

---

### Post by Sorivenul on 2009-01-27
Personally, I wouldn't suggest creating a swap partition on a flash device. The read/write rate when swapping would shorten the life of the drive considerably. Others may disagree.

Just select "Manual" in the installer, create a single partition for Ubuntu, and you should be okay. You will get warned about not creating a swap partition, but you should still be okay, provided the systems you use it on have a reasonable amount of RAM.

Also, make sure GRUB installs to the flash drive instead of your hard drive.

Hope this helps! Good luck!

---

### Post by C.S.Cameron on 2009-01-28
I use manual partitioning myself.
First partition is FAT32 so the drive will work on a Windows machine.
Second partition is ext3 with /home as mount point.
Third partition is ext3 with / as mount point.
A Fourth partition as Linux swap space is possible, but I find it never seems to get used on any machine modern enough to boot a flash drive.

---

### Post by Efros on 2009-01-28
[http://www.pendrivelinux.com/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/usb-ubuntu-tutorial-for-linux-users/)

I've used the above method to successfully install Ubuntu to a pen drive.

---

### Post by ubername on 2009-02-04
> **Sorivenul said:**
> Personally, I wouldn't suggest creating a swap partition on a flash device. The read/write rate when swapping would shorten the life of the drive considerably. Others may disagree.

Just select "Manual" in the installer, create a single partition for Ubuntu, and you should be okay. You will get warned about not creating a swap partition, but you should still be okay, provided the systems you use it on have a reasonable amount of RAM.

Also, make sure GRUB installs to the flash drive instead of your hard drive.

Hope this helps! Good luck!

Thanks for this. Part of the reason I want to use a flash drive is I have a 16Gb one from ebay for about £10, whereas many of the systems I would like to demo it on (to show how awesome it is) won't have close to that in either disk or RAM. (i know why I might not be advised to do this, but I just would like to try). Although I'm not too bothered about shortening the life of the drive I would be interested to know why, even if I could install a swap partition, this would shorten it's life, and is particularly true of flash drives.

Other posts in this thread also seem to favour ignoring the swap space,and creating a FAT32 partition. I am not bothered about making this stick a multi-purpose device able to be used by windows etc, I just want a good (persistent?) *buntu install which may be able to perform without being constrained by local RAM (and to a certain extent disk space) although obviously I can do nothing about local CPU speeds, video, sound etc.

So can anyone exlain how I can do that, and why I struggle to create the swap partition simply pointing a regular live CD at this drive and allocating partitions as usal. I have become confused when I see all the 'how to ... on a flash drive' sites, as when I installed ubuntu on a (non-flash) external USB drive, (admittedly using the hard drive swap partition), I had no problems. What is special about USB (flash or non-flash) drives?

TIA

---

### Post by timcredible on 2009-02-04
you can't use fat32 for ubuntu, it doesn't support file permissions.  also, there's nothing wrong with creating a swap partition on a flash drive - it works fine, and isn't even used unless you run out of ram, in which case if you don't have a swap partition your system crashes.  you can install ubuntu to a flashdrive the same as a hard drive, you just have to choose the flash drive when the install asks where to install grub (the default is the hard drive).  anyway, there's step by step tutorials on this on the web, i followed one and it worked well, except that the flash drive i was using was slow and made for a less than desirable experience.

---

### Post by anewguy on 2009-02-04
There are, however, extremely shorter life spans to flash drives versus a normal hard disk, as alluded to by a previous poster.  Check the read/write cycles for lifetime and you'll see.  If the system does need to use swap, it can get intense in read/write cycles and hence the warning on shortening the life span of the flash drive.  Some of this may have changed, but the last time I did any checking the read/write cycle rates for a lifetime on a flash drive was in the 100' of thousands - sounds like a lot unless you have actually studied the I-O's a normal system does, then it's not that long.

Dave :)

---

### Post by ubername on 2009-02-04
> **timcredible said:**
> you can't use fat32 for ubuntu, it doesn't support file permissions.  also, there's nothing wrong with creating a swap partition on a flash drive - it works fine, and isn't even used unless you run out of ram, in which case if you don't have a swap partition your system crashes.  you can install ubuntu to a flashdrive the same as a hard drive, you just have to choose the flash drive when the install asks where to install grub (the default is the hard drive).  anyway, there's step by step tutorials on this on the web, i followed one and it worked well, except that the flash drive i was using was slow and made for a less than desirable experience.

Hi Tim

Thanks for this. I know you can't use FAT32 for Ubuntu, I was just wandering why so many of the 'How to's' to which you refer (at least the ones I have seen) seem to recommend creating a separate FAT32 partition. The reason for this thread is that whenever I try to install to the flash drive I get the error message I posted at the start of this thread. I will make sure of course to point GRUB at the right location and I am glad you found setting up your USB drive easy.

---

### Post by Sorivenul on 2009-02-04
> **ubername said:**
> Although I'm not too bothered about shortening the life of the drive I would be interested to know why, even if I could install a swap partition, this would shorten it's life, and is particularly true of flash drives.


> **anewguy said:**
> Check the read/write cycles for lifetime and you'll see.  If the system does need to use swap, it can get intense in read/write cycles and hence the warning on shortening the life span of the flash drive.

That pretty much covers it in a nutshell for you, ubername. 

As far as actually accomplishing the persistent LiveUSB, [these directions]("http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/") rom PendriveLinux worked for me. Also, [these directions]("http://xubuntublog.wordpress.com/2008/11/07/ubuntu-from-your-flash-drive-easier-than-ever-before/") (Xubuntu-related, but still applicable) should work and explain the "usb-creator" in a bit more detail.

---

