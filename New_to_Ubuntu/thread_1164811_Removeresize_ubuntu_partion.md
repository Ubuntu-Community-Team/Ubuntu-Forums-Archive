---
title: "Remove/resize ubuntu partion"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Twanzio on 2009-05-20
I recently took the foray into Ubuntu using the Live CD and ran into a little snag. When installing Ubuntu to dual-boot with Windows, I neglected to notice the slider bar when given the option to create a partition for Ubuntu. I ended up with a tiny partition for Ubuntu and the remainider of my HDD left for XP. I want to create more space for Ubuntu but hoped to get a little advice before doing anything as drastic as screwing with the MBR or creating even more partitions. 

My  thinking was to completely remove the ubuntu partition, start from scratch with the Ubuntu Live CD and create a partition with a reasonable size. From what I've read though, I may run into issues with the GRUB loader getting erased during a resize or erase of the Ubuntu partition.
 
Any suggestions on the best way to go about removing the Ubuntu partion without messing up the boot loader? Should I restore the Windows MBR first? I already backed-up my important files to an external drive but don't want to mess up my boot since I don't have my XP restore CD. I found the program MBRFix.exe through this forum, but I'm not sure if it's the fix I need. Any help is appreciated.

---

### Post by Temposs on 2009-05-20
You don't have to do all that stuff. You should just use the partition editor on your Ubuntu LiveCD. Load up your Ubuntu LiveCD to try without installing, then find the Partition Editor under System->Administration. You should be able to then change the size of the Ubuntu partition to take up more of the hard drive. Note that doing this may take hours, so you have to be patient ;-)

Alternatively, if you want to make a LiveCD devoted to editing partitions, try the GParted LiveCD: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
It's basically the same partition editing program, but this LiveCD doesn't load up all the extra stuff that the Ubuntu LiveCD does. It's just for editing partitions.

---

### Post by Twanzio on 2009-05-20
That sounds way easier than all the ideas I had. I'll try this tonight. Thanks!

---

### Post by Didius Falco on 2009-05-20
If you are going to be resizing the Windows partition, be sure and go into Windows and defrag it thoroughly first. I'd also suggest turning of the Windows swap file until after you've resized it.

Regards,

Didius

---

