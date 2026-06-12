---
title: "does GRUB automatically update from windows bootloader?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by severedsolo on 2009-11-30
just a thought.... i have 2 different entries in my windows bootloader, windows 7, and a recovery partition which (for reasons too complicated to explain) i had to temporarily delete,

i noticed that when i boot windows, from GRUB it hands over to the windows bootloader which then asked me whether i wanted to boot windows or the recovery partition, but the recovery partition also appeared in GRUB,

If i put the recovery partition back in, will GRUB automatically find it? or will i still need to hand over to the windows bootloader to run the recovery partition?

or better yet, can i manually add it to grub if this isnt the case?

its grub2 i think.... (the one that comes with Ubuntu 9.10)

---

### Post by mbzn on 2009-11-30
Grub will not automatically update to show it, it can be manually changed.

---

### Post by severedsolo on 2009-11-30
ok thats fine, i suspected that, as it didnt delete it from grub when i deleted it from the windows bootloader... is there a kind of "idiots guide" out there to changing grub entries? (not that im an idiot.... i have just never done it before, i googled and came up with nothing or nothing for GRUB2 anyway)

---

### Post by Mark Phelps on 2009-11-30
All GRUB does is mount the partition you point to and hand over control to the MS Windows boot loader in that partition -- which is why, if you have multiple MS Windows OSs, you get a OS selection menu.

You can manually add an entry to GRUB for your recovery partition but if there is no boot loader in that partition, it will not work.

---

### Post by wirate on 2009-11-30
/boot/grub/menu.lst
 
has the entries. you can delete or add whatever you want

---

### Post by presence1960 on 2009-11-30
> **waqar said:**
> /boot/grub/menu.lst
 
has the entries. you can delete or add whatever you want

That will work for Legacy GRUB (0.97). The OP thinks he/she has GRUB 2. There is no menu.lst in GRUB 2. Here are a couple of links about GRUB 2:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by wirate on 2009-11-30
didnt know that. thanks :)

---

### Post by severedsolo on 2009-11-30
ok i sorted it, thanks for the help, i just ran update-grub and it sorted itself,

---

