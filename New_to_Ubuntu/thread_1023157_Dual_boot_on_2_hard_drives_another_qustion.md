---
title: "Dual boot on 2 hard drives another qustion"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by bazboy on 2008-12-27
Hi
After reading up on all the things that could go wrong in a two hard drive dual boot Windows XP/ Ubuntu, i am reassured to find that for most people it works as it should with no problems booting from XP or Ubuntu. My Ubuntu laptop died so i put the reformatted old laptop drive in my desktop( i want to put ubuntu back on this).The drive layout is different than most so i wondered if it would cause any problems. On the first Ide socket on the motherboard i have the windows xp hard drive and a Dvd writer with built in card reader. I will have to connect the new hard drive to the second ide socket leaving it set as Master and install Ubuntu onto it. So i have in fact two master hard drives but on different ide sockets on the mother board. Will this cause any problems on installing of booting xp or Ubuntu.I also hope Ubuntu will find the blank drive and make the install even easier.

Your opinions will be gratefully received as i do not want to mess up my system but would use Ubuntu more than windows.
Bazboy
bazboy is online now Report Post   	Edit/Delete Message

---

### Post by bumanie on 2008-12-27
Without doing any research into it, I suspect having two hard drives set to master will confuse bios and the respective bootloaders (if it gets that far). I doubt bios would have facility to allow that either. Finding a blank drive set to slave would be preferable and would work. I doubt what you are thinking of at present won't work, or at the very least will cause you lots of headaches.

---

### Post by bennachie on 2008-12-27
So long as the MBR (master boot record) remains on the same disk as the Windows installation, you should have no problem in booting Windows afterwards (and Ubuntu should find, and suggest using, the blank disk with no difficulty). 

Be careful when installing Ubuntu to specify that the master boot record is located on the XP disk. The actual Ubuntu boot partition will, by default, be placed with the other Ubuntu partitions on the second disk - a pointer to that boot partition will simply be added to the master record on the XP disk.

Don't worry too much - even if you get things wrong, Ubuntu will not overwrite the Windows partition itself without your explicit permission, and you can sort out the boot records afterwards with a neat piece of software called Super Grub Disk.

---

### Post by bennachie on 2008-12-27
Just a follow-up on the BIOS issues raised by bumanie. 

I have not personally tried the exact set-up that you have in place, but I do have three hard disks (a master and a slave HD on one IDE cable and a master HD and a slave DVD writer on the other one). That works OK for me, but YMMV. Let us know if the BIOS gets confused. Setting a hard disk to slave status is usually simple, just a matter of adjusting a small jumper on the back of the housing.

---

### Post by bumanie on 2008-12-27
I initially misread the post - Sorry. What you are suggesting should work OK - I missed the bit about the second IDE cable - even though you explained it quite clearly. Sorry again :)
I've been at work all night, think I'd better call it a day - too tired if I misread something like that.

---

### Post by theozzlives on 2008-12-27
How you going to put a laptop HD in a desktop???

---

### Post by bazboy on 2008-12-29
laptop fitted to desktop by 2.5 to 3.5 drive converter rails, plus adapter for the power and data connections.

---

### Post by BDNiner on 2008-12-29
Ubuntu should see the drive correctly, just make sure you select the correct drive when setting up the partitions so that you don't overwrite your current windows installation. Make sure to specify that the XP disk is where the MBR is located so that it is setup correctly but this can be fixed after installation.

---

### Post by bazboy on 2008-12-30
Thanks, its all clearer now.
Thanks to all who replied

---

