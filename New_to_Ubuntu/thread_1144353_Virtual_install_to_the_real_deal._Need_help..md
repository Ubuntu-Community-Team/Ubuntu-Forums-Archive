---
title: "Virtual install to the real deal. Need help."
date: 2009-04-30
forum: New to Ubuntu
---

### Post by That0neguy on 2009-04-30
So just like a lot of other people, I am done with windows. This my second experiance with linux. My first being a live CD(knopix) for about 30 minuets. When I first booted up. I was sold. The fact that my wifi rx, chipset, sound were ready to rock right of the gate with it asking to simply enable the GPU driver was amazing.
 
So I have been working on this for a couple days researching and trying to figure this out on my own. I have came to the fact I  need help. 

I am trying to get rid of my windows installation completely. I installed unbuntu by downloading and mounting it to a virtual drive (my cd-rom does not work) to install using the wubi to dual boot. Now I already had my single hard drive in two partitions. With my windows install on one, and now ubuntu on the other. Now I just don't know where to go from here. I don't really care if I am left with one partition or the original two when it is all said and done. All I really care about it getting rid of windows and soley running ubuntu in the ext3 format (that's what I want right?). I have read so much and am still left with my jaw hanging. Can someone point me into the right direction with my particular situation? Thank you.

---

### Post by kanikilu on 2009-04-30
What virtualization software are you using? Apparently this can be down with VMWare, but I don't use it and have never tried it...

[http://www.vmware.com/support/v2p/index.html](http://www.vmware.com/support/v2p/index.html)

What do you have on your linux install so far? Would it be feasible to reinstall? You say your CD-ROM is broken, but if you have a flash drive, you can use a tool call UNetbootin to create a bootable flash drive that you can install from.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by That0neguy on 2009-04-30
I actually used the iso mounting off of nero... If that's what you mean?

This is my third install of ubuntu so far lol. So it's no sweat to do another. I'm considering this flash drive thing. I think I might have one laying around. Now how would I go about that? Once I have the bootable flash ready to go? It would boot like a live cd from there wouldn't it?

---

### Post by steve101101 on 2009-04-30
it sounds like your doing a wubi install. if you mount the iso in windows. install ubuntu on the other partition and the follow the directions. it should all be peachy. then at the boot loader select ubuntu instead of windows.

---

### Post by servicetech on 2009-04-30
You're eventually going to need a CDROM for other things on your computer. Salvage one out of an old PC, or buy one for $20. It will make life a lot easier :)

---

### Post by That0neguy on 2009-04-30
Yea. I need to pick a new one up for sure. 


So I tried to do the flash drive boot. And got 'boot error'. I don't have the 'USB' option in my bios. I have 'removable' witch I'm pretty sure is the same thing? I even tried making the bootable flashdrive in widows. Same thing.

So how about just trying to do it the original way I was thinking?

---

### Post by That0neguy on 2009-05-01
Still trying to get this to work. I have tried everything. I booted using Unetbootin and came across the bug where it it was unable to unmount /cdrom. I tried transferring a wubi install to another partition and got error 17 with GRUB 'unable to mount to partition'. I'm stuck here. Am I just stuck my windows install eating me away in the background, stuck on a 60B chunk on my HDD? Not to mention not being able to format with exp3...

---

### Post by That0neguy on 2009-05-01
No one? :cry:

---

