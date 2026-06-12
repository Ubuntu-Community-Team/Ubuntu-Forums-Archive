---
title: "smart boot manager not showing"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by Primus1 on 2010-07-18
Hi, installed smart boot manager but I can't see it listed anywhere in the menues.  I want to install windows on my first hard drive (got Lucid on drive 2)
Can't get the computer to boot from cd, yes I've F2 to set BIOS to cd and saved but Grub just takes over (I've got Lucid on drive 1 also).
Gigabyte motherboard with Award BIOS.

---

### Post by mike555 on 2010-07-18
smart boot manager should be a .iso and burned as an image , that way you can use it to boot (in case yours is messed up ....... if you installed it ,it would be in the MBR and you should see it when you boot.

 perhaps I didn't understand you question ?

---

### Post by Primus1 on 2010-07-18
I got it from ubuntu software centre, installed it with synaptic, here's a screenshot

---

### Post by mike555 on 2010-07-18
Oh, that's new to me...... I always just downloaded it from the website , I would guess look in usr/bin

---

### Post by Primus1 on 2010-07-19
Not there but thanks for answering.

---

### Post by louieb on 2010-07-19
Hum - right click - bring up properties for sbm - the installed files tab is there. 

Don't know how accurate the description in Synaptic is  - never had a hard drive boot from it - not sure but believe the software you downloaded is for creating a boot floppy.  - did you see 
[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager) 

When I have had to use it in the past I created a boot floppy disk. Does this machine have a floppy drive? 

At any rate the software has not been updated since 2001 - don't know that I would trust installing it on one of my hard drives.

---

### Post by mike555 on 2010-07-19
I never had any luck with Smart bootmanager , I use GAG ....   [http://gag.sourceforge.net/](http://gag.sourceforge.net/)     every day on my milti boot system ....... just remember to install grub to the same partition as your installing linux to (because linux needs grub to boot )gag is a little strange to set up ,but easy ... and fairly nice looking.

 doesn't boot usb though.

---

### Post by Primus1 on 2010-07-19
It seems to be in /boot, here are screenshots from synaptic:

---

### Post by Primus1 on 2010-07-19
I looked at GAG but read Grub2 can cause problems with it, pity gag sounds like it has all the things I need.

---

### Post by mike555 on 2010-07-19
I use GAG everyday ,it is in my MBR, and redirects to grub 2,which is on every linux partition ...
   you can't put grub in the MBR and have it redirect to GAG , that won't work ..

---

### Post by Primus1 on 2010-07-19
I saw this:[I]

Because GAG is a pure [chain loading boot loader]("http://en.wikipedia.org/wiki/Chain_loading#Chain_loading_in_boot_manager_programs"), it requires a  kernel loader to be installed in the superblock of each bootable  partition to handle the different filesystems or kernels. This means  that users of [GNU]("http://en.wikipedia.org/wiki/GNU")/[Linux]("http://en.wikipedia.org/wiki/Linux") are  required to install [LILO]("http://en.wikipedia.org/wiki/LILO") or [GRUB]("http://en.wikipedia.org/wiki/GRUB") in the superblock of the partition in order  to be able to boot from GAG; however it seems that installing [GRUB2]("http://en.wikipedia.org/wiki/GRUB2") in a superblock is discouraged.


[/I]don't know what to make of it.

---

