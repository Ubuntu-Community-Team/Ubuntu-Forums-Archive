---
title: "first install failed miserably"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by VioletsPie on 2008-12-17
hi 

my first install of ubuntu 8.10 64 bit failed miserably, with multiple errors and buffer errors and the like.  I used the partition to give ubuntu half of my 250 gb harddrive.  More errors and finally the installation told me it had failed. 

The computer rebooted, windows went into CHKDSK, rebooted again and miraculously windows and my data survived.  I thought I had gotten what I deserved being a complete linux noob and corrupted my harddrive =P. 

Now I have the 125 gb partition invisible and I downloaded a freeware partition program to detect it. 

My question: 
Do I delete the partition to prepare for another attempt at install? 

What went wrong? I am going to re-download the 32-bit .iso and burn it and this time follow the instructions for checksum and whatnot (whatever that means) and use a different disc. 

I've got a lot of free time for an entire month before I go back to school and have been teaching myself a lot about computers. It's high time I learn how to use linux and ubuntu seems the way to go for noobs. 

Thanks! 
VioletsPie

---

### Post by taurus on 2008-12-17
Use gparted from the LiveCD (System -> Administration) and format that free space to ext3.  Now see if the installer can detect that partition.

Also, at the initial menu, pick the scan cd for defects to make sure the CD is good before you attend to install Ubuntu with it.

---

### Post by VioletsPie on 2008-12-17
Thanks for the quick reply!

---

### Post by xjcannonx on 2008-12-17
I agree with Taurus, also when you burn the iso, do so at the slowest speed, with disc-at-once(or whatever your burning program calls it) instead of track at once

---

### Post by evilkastel on 2008-12-17
taurus's advice is the best, and the one after too. but if you still have issues or as a preventive messure, check the MD5 of the file, to check integrity.

---

