---
title: "GRUB question"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Al Fischer on 2009-02-23
I have loaded Intrepid server and considering I started only about 10 days ago have it almost like I want. What I am attempting to do is save an image created with Acronis True Image and restore it to a second partition on the same drive or copy the first partition to empty file space on the same drive. This will give me flexibility to try things without concern for destroying my load. What should the menu.lst in Grub look like to go to the second partition on the drive?

The standard supplied one works for the first partition.

title		Ubuntu 8.10, kernel 2.6.27-11-server
uuid		1e22d298-38b4-48e2-b69e-d15c04458b1b
kernel		/boot/vmlinuz-2.6.27-11-server root=UUID=1e22d298-38b4-48e2-b69e-d15c04458b1b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-server
quiet

How would I modify this to boot from the second menu entry?

---

### Post by spiderbatdad on 2009-02-23
to do this I believe you will need to run an installation disk or partitioner and actually create the space that way; that is, you will make a root / ext3 filesystem, for example, to host what sounds like an entire os you want untouched. So just boot your live cd and make another installation on unused space. Grub will automagically take care of the rest.

---

### Post by BDNiner on 2009-02-23
Good idea Spidebatdad. I don't think you will be able to restore the ubuntu image though. My experience with ubuntu and acronis did not work. Acronis would try and mount the partition and then give me errors instead or restoring like i requested. But that was with verion 6 i believe. It was a couple years ago.

---

### Post by Kellemora on 2009-02-23
Hi Al

Maybe I don't understand what you are asking?

In any case, I only see ONE entry in your Grub file.

A second would look like the first only have it's OWN UUID and boot info.

When Grub loads, you would then pause and move the selector down to the second entry to boot that one.
OR move the second entry to where the top entry is, moving the top entry to second place so the top one is the one that boots automatically.

Of course, your other partition would have to be bootable in order to boot from it too!

TTUL
Gary

---

### Post by Al Fischer on 2009-02-23
Acronis is a different beast since Ver 6!
I am using Ver 11. (with the update it needed to work!)

It actually restores to free space and I have tested it on a bare drive. 100%. (unfortunately it doesn't like ext3 so works in bit by bit,  and Sloowly...)

I am trying to avoid doing any additional installs as I have been using Windows for years and backing it up this way. So I hose-up my system and all I do is put back the image from last week and then restore email from it's own backup. Excellent way when trying new software.

I did read one thread on copying the 1st partition with gparted and tried it but I need to UNDERSTAND grub. (and I will, eventually!)

---

### Post by Al Fischer on 2009-02-23
The sample is cut-paste from the file. It boots to the first partition on the hard drive. The image on the 2nd partion is a copy of the 1st. What I am asking is what this should be for it to boot from the second partition. I assume it would then be placed on the menu for the 2nd boot option.

In reality I do not understand the whole grub process. I downloaded the manual and am planning on studying it.

I am in a position now to do whatever to the system as I can restore it in less than 1/2 hr. This project is as much a learning process as it is to build a server. (however a server would be quite handy for website work and media streaming)

---

### Post by Al Fischer on 2009-02-23
maybe my question should be "how would I determine the UUID for the second partion and how should it be stated?"

---

