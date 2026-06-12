---
title: "Major help need booting"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by lamex on 2009-08-28
I'm running an Asus x83vb, Vista dual core 2g, 4g DDR, Nivida 9300m gs 512mb 250HDD.

I installed ubuntu about a few months ago, I'm new to linux. A few nights ago i shut down my latop and turn it back on and everything was mess up. I try to boot vista and it boots it up to where the login screen is BUT! its a black screen and i can move my mouse. Then i try to login to my ubuntu side of my hard drive and it wont load up. i try to recover and it goes to busy box. Busy box v1.10.2 is the only thing i can run on my laptop atm. I try deleting everything and reinstalling windows first it took but i restarted and it did the same thing. Its seems that i now don't have room on my hard drive to do anything. 

From what i figured whats happening is my hard drive is full and cant make temp files, also i see (syslinux 3.36 boot: ) sometime when i have been trying to boot, guessing that means MRB is no longer on my laptop. I want to fix all of this and get vista and ubuntu back on. 

YES I AM A  SUPER NOOB!!!

---

### Post by Mrandersonjr on 2009-08-28
Try running a live cd,then,open a terminal (make sure you are connected to the internet) and type in 

sudo apt-get install bleachbit

Once it's installed then type: sudo bleachbit

and run it,it will clean all temp files if that is the problem.

---

### Post by louieb on 2009-08-28
Sounds like hardware. Hard drive (my guess) or memory.  Do you have a live CD? Can you browse the hard drive with it?  

Recommend you get a [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") and run GsmartControl. - you can run the hard drives built in tests - that will tell you a lot about the health of the hard drive.

---

