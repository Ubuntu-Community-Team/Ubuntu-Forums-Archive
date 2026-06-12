---
title: "how to remove windows from side by side install"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by dooge on 2010-10-21
So i installed Ubuntu and have been using it for about a week now. I searched the forums for this answer but mainly see people wanting to remove ubuntu, i want to know if its possible to remove windows from a side by side install?

Thanks for reading this,

Dooge.

---

### Post by wojox on 2010-10-21
Sure, insert your Live CD and open G-Parted and delete your Windows Partitions.

---

### Post by dooge on 2010-10-21
> **wojox said:**
> Sure, insert your Live CD and open G-Parted and delete your Windows Partitions.

Wow, talk about a fast response! Thank you. 

I should have mentioned that I used the WUBI(?) flashdrive creator. Would this still be performed the same way?

---

### Post by wojox on 2010-10-21
No wubi actually runs in Windows. You would need to just download a Ubuntu version of choice and install it completely.

---

### Post by dooge on 2010-10-21
Ah, so it would be a case of completely re-installing? Well, okay then :) Thanks for the help again!

---

### Post by trikster_x on 2010-10-21
If you are going to completely remove windows from your hard drive, I would suggest you download and run magic jelly bean before hand.  It will give you the registration key of software like photoshop, microsoft office and windows itself.  That way if you should need to install windows again you can. I know, I wouldn't either, but sometimes I run into a program that just won't quite run right in wine and has no decent working equivalent in ubuntu (playstation emulators anyone?).  I avoid logging into windows like it'll set me on fire, but once in a while I still need it to do stuff.

---

### Post by dooge on 2010-10-21
Ah, thanks for the advice, trickster. I will definitely do that.

---

### Post by mastablasta on 2010-12-03
> **wojox said:**
> Sure, insert your Live CD and open G-Parted and delete your Windows Partitions.

Sorry to bump this thread like this but i had it's  URL in my email, to use when the time comes.

I think now it's the time as i need more space for ubuntu. I backed up most of things, some will be backed up tomorrow. 

Questions i have is will this also remove it from GRUB menu on the start or make it all look like a "clean" Ubuntu install (no windows or traces of it)?

---

### Post by uRock on 2010-12-03
If you delete the Windows partition, then run **sudo update-grub**, then the Windows listing will disappear from the grub menu and if that was the only other OS, then your system should start skipping the boot menu and start booting straight into Ubuntu.

---

### Post by mastablasta on 2010-12-04
it doesn't skip the boot.

aslo i need to figure out how to add this partition to linux (increase linux partition size....)

---

### Post by ChuckyDuckster on 2010-12-04
> **mastablasta said:**
> it doesn't skip the boot.

aslo i need to figure out how to add this partition to linux (increase linux partition size....)


You will need to use a LiveCD, because you are trying to resize the linux partition. It won't let you do that while you are running your operating system from that partition.

---

