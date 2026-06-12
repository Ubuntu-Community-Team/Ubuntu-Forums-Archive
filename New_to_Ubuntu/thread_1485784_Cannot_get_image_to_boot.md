---
title: "Cannot get image to boot"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Brad wilkinson on 2010-05-17
Hello,

I've loaded 10.04 LTS on to my new pc, but now I would like to upgrade to 64bit as the pc is all-new and should be fine running 64bit...

PC is as follows: 
Gigabyte GA-880GM-UD2H v4 bios. 
Phenom II x6 1055.
8gig ram in 2*4gig sticks. 
2tb hdd, dvd drive both on sata.
on board video for now.
current kernel Linux 2.6.32-22-generic-pae


I downloaded the torrent for 10.04 amd x86-64 .iso and burnt it to cd using Brasero. Rebooted with the CD selected as 1st boot device. Boots from the hdd. Odd, as the cd looks fine when I browse to it from the desktop.

Then I used startup disk creator to add it to a USB disk to try that. Looks like it worked fine, I can browse to it fine and see all the files there. Then I modify the bios so that USB hdd is the only boot option. So the system then boots from the hdd......

What am I missing/doing wrong? :confused::confused::confused:

---

### Post by Riaku on 2010-05-17
When your PC first boots up at the BIOS loading screen there should be two options one being setup and the other being boot selection. Hit the key that corresponds to boot selection ( normally F10 or F12) and it should take you to a menu to choose which device to boot off of. If everything is configured correctly it should work.

---

### Post by zeekoman on 2010-05-17
Sometimes BIOS's won't recognize bootable media unless you manually select what to boot from (as suggested above).

---

