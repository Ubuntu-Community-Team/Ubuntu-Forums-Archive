---
title: "GRUB fix"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by lengo on 2009-10-23
I dual boot XP and Ubuntu. Or at least I used to... I was trying to resize partitions with GParted (sound familiar yet... ?) and inadvertently deleted the Ubuntu partition. On boot I got Error 22. After searching I found that it might be possible to do 'fixmbr' from an XP install disk recovery console. XP recovery console reported that "Setup did not find any hard disk drives installed in your computer". Sigh... My next approach was to try to repair GRUB from a LiveCD. sudo grub, find /boot/grub/stage1 returned Error 15: File not found. I found some instructions [_here_]("http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-22-deleted-partition-377590/page2.html") that suggest to do: sudo lilo -M  /dev/sda mbr. Another suggestion was to reinstall Ubuntu and create a new GRUB. Any advice would be much appreciated (obviously).

---

### Post by ranch hand on 2009-10-23
Do you have a LiveCD?
EDIT
Sorry I can't read.

Can you read your files through the live CD?

If so post your /boot/grub/menu.lst.

---

### Post by pgar23 on 2009-10-23
Do you still need XP? if so, why not back-up your XP drive and then re-install both XP and Ubuntu?? Sounds like a logical fix.

That's only if you have to keep dual-booting with XP and Ubunut. Otherwise why not just use Ubuntu completely? The one and only reason I kept XP on my machine was because I needed iTUNES and that wasn't compatible with Linux. But now that I found out how to work it with Ubuntu i only use that.

---

### Post by pgar23 on 2009-10-23
P.S. you created two posts for the same issue. GRUB fix. 
ONLY ONE POST IS NEEDED. We are more than happy to help you, so it is not necessary to double post. k. Thanks.

---

### Post by lengo on 2009-10-23
Thanks for showing up, ranch hand. I was just about to add a "PLEASE" to my initial post!

Unfortunately, I cannot see any files from the Ubuntu partition that I deleted--they's gone... I can see boot.ini in the Windows partition. Does that help?

Also, does the 'reload Ubuntu and work with a new GRUB' option I mentioned above hold any promise?

Thanks for offering to help!

@pgar23: yes, I still need XP, ergo my attempt to restore it... Enjoy your iTUNES.

---

### Post by egalvan on 2009-10-24
SuperGRUB LiveCD is usually able to fix these MBR problems...
give it a try.

---

### Post by lengo on 2009-10-24
Sorry for the double post. I've got a brutal connection (developing world country), and the page stalled on my first post... I thought it had failed so I reloaded it. Guess the first one went through after all.

---

### Post by ranch hand on 2009-10-24
You have no grub to fix.  Ubuntu is gone.  Did you loose data?

Was this installed on one partition or two?

You are going to have to reinstall Ubuntu, you can do it right where it was.  You are safer with / on pne partition and /home on another.

---

### Post by Dullstar on 2009-10-24
I can try SuperGRUB disk, I suppose, because what's there to lose?  Windows XP no longer boots. [sarcasm] Thanks so much, Grub2! [/sarcasm]

---

### Post by ranch hand on 2009-10-24
If you want Ubuntu on there, reinstall and your boot problems will be fixed.

SuperGrub disk may help you boot XP.

Grub2 is not the problem here, wiping a partition with gparted is.

Were you partitioning from the drive you were partitioning.  This should not be done.  Use the live CD or gparted from another drive.  Using Gparted from the partition you are on is like cutting off the limb you are sitting on.

---

### Post by lengo on 2009-10-24
Feeling the need to report back on my experience... SuperGRUB solved my problem (thanks so much, egalvan!). My critical data was in Windows, so that was my highest priority. And SuperGRUB got it back quite painlessly. I can reload Linux if I need to, but there was nothing there I *needed* to save (thankfully). Thanks for all your help. Really. Saved me from a stupid mistake (cutting off the branch I was sitting on, as ranch hand put it :roll:).

---

