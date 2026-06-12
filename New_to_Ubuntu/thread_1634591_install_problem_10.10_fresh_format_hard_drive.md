---
title: "install problem 10.10 fresh format hard drive"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by henry cow on 2010-11-30
I am trying to install 10.10 on an old, but freshly re-habbed desktop. I will not go into the details, but I have a 60GB hard drive, formatted with a 37GB primary ext4 partition, a 3GB swap, and a 20GB FAT32 partition.

The drive is clean with absolutely nothing on it.

The computer will POST and almost boot of a CD, the "ubuntu" logo and the red and white dots march across the screen, but eventually I get a black screen and the error message:

"unable to find a medium containing a live file system"

and a prompt

"inittramfs"

 What does this mean, and what do I do?

Thanks!

---

### Post by nhasian on 2010-11-30
nothing to do with your hard disk. you can even boot off the liveCD even if there is no hard disk in your computer.  Make sure you recorded the cd image to a CD and not to a DVD.  burn at slowest speed possible.  if still unable to boot from cd, try the ubuntu alternate cd instead of the liveCD.

---

### Post by Liverbones on 2010-11-30
I concur with what nhasian said: this is not a problem with the hard drive. In fact, you're not even touching the hard drive yet; initramfs is essentially a compressed image of a bootable system that gets loaded into memory before the actual root filesystem is mounted. As far as I can tell, this means that the boot process can't proceed past the initramfs stage because it can't find the next stage in the boot process, which points to a problem with the Live CD. But the hard drive has nothing to do with this part of the process.

In fact, the hard drive has little to do with the system running off of a live disc period until you decide to *install* it to the hard drive.

I could, of course, be completely wrong. But that's what it sounds like to me.

---

### Post by henry cow on 2010-11-30
Thanks guys. 

I thought that burning a new CD from the .ISO file would do it, but no.

I still get the same message with a fresh new CD.

Any other suggestions?

---

### Post by Rex Bouwense on 2010-11-30
OK, Did you md5sum the downloaded ISO?  If you got two CDs neither of which will boot, you may have a bad download.  
Nhasian told you to try an alternate install CD.  You will have to download that and check the md5sum.  Some computers will not boot from a Live CD.

---

### Post by henry cow on 2010-12-01
Thanks for your help, but there must be some other problem. 

I downloaded the 32-bit version of Lucid and it gave me pretty much the same result, but not exactly. Here is what I got:



[B][SIZE=3]BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

(initramfs) Unable to find a medium containing a live file system.
[/SIZE][/B]


The computer is an old Compaq with an Athlon 1100 and 512 MB of ram, and some USB ports. It has a DVD player and a CD-RW which seem to work because the Ubuntu logo comes up for a while as it loads.

I don't mind formatting the hard drive again, using the USB drive, or whatever. 

Rex mentioned that some computers will not boot off a Live CD. What do you do then? I can plug the drive in externally to this working computer and copy files, but is there a way to do that for a boot drive?

Thanks again

---

### Post by Liverbones on 2010-12-01
That's correct, some computers simply will not boot from the live CD; that does not mean that Ubuntu cannot be installed on those computers. Your best bet in those cases is to use the alternate CD, which I've been able to load on all kinds of computers without a problem. It's rather basic, as there's no live desktop, but you can still install the system easily with the alternate CD.

Also, if the computer's BIOS allows you to boot from USB, you may have more luck booting to the live desktop from a USB device than you are having using a CD (perhaps there's a problem with the CD reader). That is, of course, dependent on the system even allowing a USB boot, which it may not do, considering its age. But I can tell you that I've personally installed Ubuntu using the alternate CD on computers that are almost a decade old, with significantly lower specifications than you have presented here.

And I really do hope that this works out for you. :)

---

### Post by NCLI on 2010-12-01
[Here is a link to the alternate cd]("http://www.ubuntu.com/start-download"). It is a little spartan, but it should work.

---

### Post by henry cow on 2010-12-04
Thanks for all the suggestions.

I took the hard drive out, and used my other computer to delete and create a single partition on it.

Started again, and installed Ubuntu on a new partition I created. From there, I shrank that partition and left unallocated space. 

Later, I installed "gparted" and created a FAT32 partition with the extra space and juggled my swap file to make it bigger.

This has all worked to my satisfaction, but I must say that the instructions and procedures involved in gparted are very confusing and unnerving. I have been down this trail half a dozen times over something less than a year, on 4 different computers, and although it should be becoming familiar by now, what words I read on the screen do not accurately depict what I am trying to do.

This is an area that should be made more user-friendly if the masses are ever going to be expected to start using this OS.

Thanks to all the volunteers donating their time and energy to this.

---

