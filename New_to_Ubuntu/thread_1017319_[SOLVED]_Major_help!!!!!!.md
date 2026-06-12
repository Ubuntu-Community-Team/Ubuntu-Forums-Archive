---
title: "[SOLVED] Major help!!!!!!"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by SportsGuy2 on 2008-12-20
I installed ubuntu on my flashdrive and now of requires my flashdrive to be plugged in for it to work. Somebody please help me!

---

### Post by eagle416 on 2008-12-20
Please rephrase that?

---

### Post by SportsGuy2 on 2008-12-20
I installed ubuntu on my flashdrive, and now i have to have my flashdrive plugged in for the bootloader to work, so is there any way i can have the bootloader on the computer instead???

---

### Post by adult swim on 2008-12-20
what is the os on the hard drive?

---

### Post by SportsGuy2 on 2008-12-20
xp, thank you for helping, (and im from ky too!)

---

### Post by SportsGuy2 on 2008-12-20
is there anyway that i can completely take the bootloader off??

---

### Post by adult swim on 2008-12-20
if you have your xp cd, youll need to boot off of it and then go to the recovery console.  once you are there you need to enter in ```
fixboot

fixmbr
``` one at a time.

---

### Post by SportsGuy2 on 2008-12-20
I can't find it! :( i'll keep looking though

thanks again for helping

---

### Post by handydan918 on 2008-12-20
If you can't find your xp disk, try [this]("http://www.ultimatebootcd.com/")

---

### Post by adult swim on 2008-12-20
if you cant find it, you can download super grub disk and write the iso to a cd.  then you can boot the super grub disk and there is an option to restore windows MBR which is what you want to do. 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
once you have that straightened out you may want to check out this link to make your flash drive bootable.
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive).

---

### Post by SportsGuy2 on 2008-12-20
What am I supposed to do after I boot it up?

---

### Post by SportsGuy2 on 2008-12-20
is anybody still there???

please help :(

---

### Post by eagle416 on 2008-12-20
did you get the Super GRUB disk, Windows XP disk, or are you in USB Ubuntu?

---

### Post by SportsGuy2 on 2008-12-21
the super grub disk. thank you so much

---

### Post by handydan918 on 2008-12-21
> **SportsGuy2 said:**
> What am I supposed to do after I boot it up?

after you boot WHAT up?

---

### Post by SportsGuy2 on 2008-12-21
the super grub disk. how do you do that thing you told me??

---

### Post by eagle416 on 2008-12-21
Ohhhhh. nowww....... how does this gooooo........ The super grub disk gives you a temporary bootloader, right? in Super Grub disk look for an option to restore the Windows MBR.

---

### Post by SportsGuy2 on 2008-12-21
okay, i'll try. brb to tell if it works

---

### Post by adult swim on 2008-12-21
you need to select windows from the menu and then select fix boot of windows

---

### Post by SportsGuy2 on 2008-12-21
Can you give me a link. To make sure I have the right thing?

---

### Post by adult swim on 2008-12-21
[http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)

---

### Post by SportsGuy2 on 2008-12-21
It's booting into windows :) thank you SO MUCH!!!

Ill have to figure out Linux another day :) 

Thanks again!

---

