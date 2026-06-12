---
title: "Ubuntu on USB + Update manager"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by zedsdead on 2010-03-22
Hello I installed 9.10 on a 4GB USB stick using the live CD and the menu option USB Startup Disk Creator. 1GB Persistant. First thing I did on my new USB system was to run Update Manager. Selected all updates and then let it apply the updates. 

I seemed to have messed my USB system. It won't boot. (I did this twice to make sure it wasn't user error)

Am I not supposed to update a USB install?

My purpose is to have a portable OS that I can run on any computer. That has my software, bookmarks, etc. on it.

Thanks!
Zed

---

### Post by 2hot6ft2 on 2010-03-22
Did you receive an error? If so what was it? Did it drop you to the initramfs prompt?
Keep in mind that using the USB Creator with persistence when you do updates the changes that can be applied outside the iso are saved in a file, the iso itself is not changed and that's where I think the problem lies.
I did a full usb install and it booted fine without the hard drive in the pc (I removed the drive so no changes could be made to my hard drive). If I put the hard drive in and tried booting to the usb it would drop me to the initramfs prompt.

What I ended up doing was a full install of 8.10 to the usb then upgrading to 9.04 then to 9.10. Now it works like it should regardless of whether or not the hard drive is in the pc. Also since the whole idea is to be able to use the usb in other machines if I update a kernel I do it without a hard drive in the pc so grub wont update and reflect the OSes that are on the hard drive.

The USB Creator is designed so you can use a usb flash drive instead of burning a cd I don't think it was actually meant for using it as an OS.

Got to go check something.

---

### Post by Directive 4 on 2010-03-22
try to install from the live cd,

the option that says install ubuntu, then select the usb as the drive to install to.

don't boot the live cd (try ubuntu without any change)

remember to make the usb bootable.

---

### Post by wilee-nilee on 2010-03-22
> **Directive 4 said:**
> try to install from the live cd,

the option that says install ubuntu, then select the usb as the drive to install to.

don't boot the live cd (try ubuntu without any change)

remember to make the usb bootable.

A 4 gig thumb is not workable for a full install device 8 gigs at the least would be much better for a portable.

The last 4 or 5 times I fully installed to a thumb the boot was set to be set in the HD of the computer so be careful to make sure you check the advanced button on the last gui on the install, and point the boot at the USB.

---

### Post by Directive 4 on 2010-03-22
> **wilee-nilee said:**
> 

The last 4 or 5 times I fully installed to a thumb the boot was set to be set in the HD of the computer so be careful to make sure you check the advanced button on the last gui on the install, and point the boot at the USB.


yes, this is the way, however i have a 4gb usb drive running ubuntu by the above method with zero problems. lots of room left over to.

---

### Post by wilee-nilee on 2010-03-22
> **Directive 4 said:**
> yes, this is the way, however i have a 4gb usb drive running ubuntu by the above method with zero problems. lots of room left over to.

A full install of Ubuntu is 2.5 gigs you do the math.

---

### Post by 2hot6ft2 on 2010-03-22
> **wilee-nilee said:**
> A 4 gig thumb is not workable for a full install device 8 gigs at the least would be much better for a portable.

The last 4 or 5 times I fully installed to a thumb the boot was set to be set in the HD of the computer so be careful to make sure you check the advanced button on the last gui on the install, and point the boot at the USB.
Yeah, that too, and what everyone else said about the boot loader if it was going to be a full install. Seems the USB Creator works for some and not for others with persistence. Had to run fix something before I could finish.

---

### Post by Directive 4 on 2010-03-22
4 - 2.5 = 1.5 left over.

that good nuf maths for ya

---

### Post by zedsdead on 2010-03-22
Thanks Much!

I did not realize that it was meant as a live CD replacement.

---

### Post by C.S.Cameron on 2010-03-22
Updating does not work well with a "persistent" thumb drive, the kernel can't be easily updated as most everything is in an image file except the persistence file casper-rw.
The casper-rw file is limited in size to 4GB being FAT32 FS and it fills up quickly if you do updates.
If you make an ext4 partition and label it casper-rw you can have as much persistence as disk size allows.
You can also upgrade to the next version of Ubuntu without loosing any of your saved data or programs.
The advantage of a "persistent" install is that it is only 0.7 GB vs 2.3 GB. but that is without the Casper-rw file.

---

### Post by wilee-nilee on 2010-03-22
> **Directive 4 said:**
> 4 - 2.5 = 1.5 left over.

that good nuf maths for ya

Very good I will put a gold star on your chart, you may understand yet. ;)

---

### Post by wilee-nilee on 2010-03-22
> **zedsdead said:**
> Hello I installed 9.10 on a 4GB USB stick using the live CD and the menu option USB Startup Disk Creator. 1GB Persistant. First thing I did on my new USB system was to run Update Manager. Selected all updates and then let it apply the updates. 

I seemed to have messed my USB system. It won't boot. (I did this twice to make sure it wasn't user error)

Am I not supposed to update a USB install?

My purpose is to have a portable OS that I can run on any computer. That has my software, bookmarks, etc. on it.

Thanks!
Zed

I think your mistake was not setting the persistent all the way to the right giving you about 3.1 gigs to write to with updates etc. You could probably go 2 gigs persistent and get by but I would use the whole thumb. I have the same setup with a 4 gig thumb and a rsync lucid iso on it in home with space.

Edit: Actually I think part of the problem might be the amount of updates for 9.10 is part of the problem. This way of using a usb can be portable, but you have to realize that it is still reading the ISO and the downloaded updates instead of straight files on a HD or Thumb.

---

### Post by Directive 4 on 2010-03-23
> **zedsdead said:**
> 

My purpose is to have a portable OS that I can run on any computer. That has my software, bookmarks, etc. on it.




me thinks it's you who may understand yet

i read he does not want an iso, but a fully function os, on a usb stick, 


> **wilee-nilee said:**
> 

A 4 gig thumb is not workable for a full install device



for this (a full install) a 4gb usb stick is fine, 

on mine i have 4 kernals and as many updates as i like, with no problems.

:popcorn::popcorn::popcorn::popcorn:

---

