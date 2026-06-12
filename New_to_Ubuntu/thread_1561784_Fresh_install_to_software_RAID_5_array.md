---
title: "Fresh install to software RAID 5 array"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-08-26
Hey,

I'm currently working on a fresh install of Ubuntu on a RAID 5 array, and I'm looking for some clarification.

Right now, I'm using the Live CD Desktop (booted off of a flash drive) to partition the drives properly, and I've installed mdadm so I will be able to build the array.

So, once I build the array, will I be able to click on the "Install Ubuntu 10.04.1 LTS" icon on the desktop of the Live CD, and have the graphical installer see the new RAID?

I've been using [http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/](http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/) as a guide, but it doesn't say anything about INSTALLING to the new array. Besides what's included in this article, is there anything that needs to be done to keep the array together after a reboot?

All help is greatly appreciated.

Thanks a lot,
Kurt

---

### Post by jkurtisr32 on 2010-08-26
So...

It seems that there are a bunch of ways to create a RAID 5 system to store data, but when it comes to putting an operating system on the array, **** gets ruff.

It seems that in order to rebuild the array at boot up time, you need to have a separate /boot partition on one of your disks. In my opinion, this fact sort of defeats the purpose of RAID 5. Using level 5, the array will still function if one disk fails, but with the necessity of the /boot partition, failure of the drive housing the /boot will result in a complete failure.

Can someone verify that the above is true?

I think what I might do instead is set up a RAID 0 for my operating system, then set up a RAID 1 for my personal files.

-Kurt

---

### Post by skatinjj on 2010-08-26
> **jkurtisr32 said:**
> So...

It seems that there are a bunch of ways to create a RAID 5 system to store data, but when it comes to putting an operating system on the array, **** gets ruff.

It seems that in order to rebuild the array at boot up time, you need to have a separate /boot partition on one of your disks. In my opinion, this fact sort of defeats the purpose of RAID 5. Using level 5, the array will still function if one disk fails, but with the necessity of the /boot partition, failure of the drive housing the /boot will result in a complete failure.

Can someone verify that the above is true?

I think what I might do instead is set up a RAID 0 for my operating system, then set up a RAID 1 for my personal files.

-Kurt

[Read this.]("http://www.pcguide.com/ref/hdd/perf/raid/levels/singleLevel5-c.html")

In a RAID 5 configuration, data is stripped down and spread across several hard drive so that when one fails, another can go in its place and get data written to it to keep the parity going.

---

### Post by jkurtisr32 on 2010-08-26
> In a RAID 5 configuration, data is stripped down and spread across  several hard drive so that when one fails, another can go in its place  and get data written to it to keep the parity going.

Right, but it seems that if you're going to have the array reassembled at boot up, you need to have a /boot partition on one of the disks. If THAT disk were to fail, you'd be screwed. I'm trying to confirm whether my statement is true or not

---

### Post by skatinjj on 2010-08-26
> **jkurtisr32 said:**
> Right, but it seems that if you're going to have the array reassembled at boot up, you need to have a /boot partition on one of the disks. If THAT disk were to fail, you'd be screwed. I'm trying to confirm whether my statement is true or not

In theory, the /boot partition should be stripped down across disk and if one fails, the others can boot as well.

I only say in theory because I do not use RAID, just know about it, book smarts.

Oh software RAID, you'll have to some searching on that, not sure it can be done properly with drivers and software needing to be loaded first.

---

### Post by jkurtisr32 on 2010-08-26
> In theory, the /boot partition should be stripped down across disk and if one fails, the others can boot as well.

That would be awesome. However, the author of the following article said that he had to create a separate /boot partition in order to allow the grub to boot (See step 5, item 1):
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
Granted, he was building a RAID 0 array, so if one failed, he'd be screwed anyways.

I'm still trying to figure out how to actually install to the 5 array. All the tutorials I've been able to find on RAID 5 have been for file storage arrays and NOT for operating system filesystems

---

### Post by skatinjj on 2010-08-27
> **jkurtisr32 said:**
> That would be awesome. However, the author of the following article said that he had to create a separate /boot partition in order to allow the grub to boot (See step 5, item 1):
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
Granted, he was building a RAID 0 array, so if one failed, he'd be screwed anyways.

I'm still trying to figure out how to actually install to the 5 array. All the tutorials I've been able to find on RAID 5 have been for file storage arrays and NOT for operating system filesystems

Well RAID 5 is meant for storage, not really booting.

To install to it, you would need the software to run and build the array before installing.  maybe possible with the alternate install cd, I'd look into that.

Also, once its installed, you could look at making a bootable usb drive to the load the drivers and software to build the array, then boot from the array.

---

### Post by jkurtisr32 on 2010-08-27
I wonder if it would be possible to boot to the desktop version of Ubuntu (say, installed on a flash drive), then install mdadm and build the array. Perhaps I could then use UNetbootin to install a second version of Ubuntu on the array and try to copy the necessary assembly information over from the flash drive.

Either way, I don't fully understand how the array is going to be built if the information required to rebuild the array is located on the array.

I think i might just go with a RAID 0 array for the op sys and a RAID 1 array for the inportant personal files.

-Kurt

---

### Post by skatinjj on 2010-08-27
> **jkurtisr32 said:**
> I wonder if it would be possible to boot to the desktop version of Ubuntu (say, installed on a flash drive), then install mdadm and build the array. Perhaps I could then use UNetbootin to install a second version of Ubuntu on the array and try to copy the necessary assembly information over from the flash drive.

Either way, I don't fully understand how the array is going to be built if the information required to rebuild the array is located on the array.

I think i might just go with a RAID 0 array for the op sys and a RAID 1 array for the inportant personal files.

-Kurt

Use a bootable flash drive to hold all the information required for the array.  downside, you will always need the flash drive and have it plugged in.

---

### Post by jkurtisr32 on 2010-08-27
> Use a bootable flash drive to hold all the information required for the  array.  downside, you will always need the flash drive and have it  plugged in.

I think if that were the case, then I would just make a partition on one of the drives in the array to hold that information. If that drive failed, the system would be finished, but at least my odds would be better than with a RAID 0 array.

I need to continue digging to try and figure out how to do this. It seems that I will need to use the Alternate CD for sure. I wonder if anyone knows if the Alternate Install CD supports RAID 5?

---

### Post by skatinjj on 2010-08-27
> **jkurtisr32 said:**
> I think if that were the case, then I would just make a partition on one of the drives in the array to hold that information. If that drive failed, the system would be finished, but at least my odds would be better than with a RAID 0 array.

I need to continue digging to try and figure out how to do this. It seems that I will need to use the Alternate CD for sure. I wonder if anyone knows if the Alternate Install CD supports RAID 5?

Not sure if you have seen [this]("https://help.ubuntu.com/community/Installation/SoftwareRAID#Installing"), but it is a good guide to getting raid up and running.

And yes the alternate install cd supports RAID 5.

---

### Post by jkurtisr32 on 2010-08-27
Got it up and running.

I did need to place a /boot partition on my first HDD in the array, but I suppose that it's an acceptable risk.

The Alternate Install did allow me to get RAID 5 up, as you mentioned. I also put 2 more partitions in RAID 1 for valuable documents with added file security. Works well.

Thanks for the help, dude.

-Kurt

---

### Post by skatinjj on 2010-08-27
> **jkurtisr32 said:**
> Got it up and running.

I did need to place a /boot partition on my first HDD in the array, but I suppose that it's an acceptable risk.

The Alternate Install did allow me to get RAID 5 up, as you mentioned. I also put 2 more partitions in RAID 1 for valuable documents with added file security. Works well.

Thanks for the help, dude.

-Kurt

Not a problem, glad to help with what I could.

Good learning experience for both :p

---

