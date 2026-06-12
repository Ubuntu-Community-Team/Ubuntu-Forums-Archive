---
title: "Cannot get into BIOS on dual-boot win7/Ubuntu (Eee PC)"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by sideshoweric on 2010-10-13
Sorry if this is the wrong place to post this. I searched and was not able to find the answer I needed either.
 
I have an Asus 1005HAB Eee PC that came with win7 starter preinstalled.
I've got it dual booting with Ubuntu 10.04
I just upgraded my memory from 1 > 2 GB.
Win7 is not recognizing the full 2GB, still reads 1GB.
Ubuntu also shows 994.1 MiB
 
As far as I know the Eee PC requires you to enter the BIOS, then exit and restart for it to 'see' the full 2GB of RAM.
 
When the computer restarts normally, I get the Windows Boot Manager screen with only the options for Windows / Ubuntu / Memory test
If I select Ubuntu from there, I get the GRUB screen.
If I select Windows it simply starts Windows.
 
I've tried holding F2, F8, F12, Esc, or Del as the computer starts and I can't seem to get into the BIOS.
 
Does anyone else know how to get around this issue to touch the BIOS?
 
Thanks in advance for your help.

---

### Post by sideshoweric on 2010-10-13
Thought of something else to try.  Running the memory test option on the Windows Boot Manager now to see if that makes the computer see the full 2GB.

---

### Post by Quackers on 2010-10-13
Do the specs allow for more than 1GB of ram? Just checking :-)

---

### Post by sideshoweric on 2010-10-13
They're supposed to.  And reviews on Amazon list this issue specifically - the having to go into the BIOS to have the memory recognize properly thing, that is.  ;)

---

### Post by sideshoweric on 2010-10-13
Memory test complete, no issues with the memory, but the system properties still show only 1GB.

---

### Post by Quackers on 2010-10-13
Did you try removing the battery for a few minutes?

---

### Post by Quackers on 2010-10-13
Did you get a manual with it? Alternatively you could go to the website and download one. At least you'll know for sure which key to press to get to the bios.

---

### Post by sideshoweric on 2010-10-13
Okay, I got it.
 
I did pull the power/battery just now, just to see...  On restart, I hit Esc on the windows boot manager.  That seemed to give me more time before it popped up again.  Tapping F2 very quickly during that time brought me to the BIOS.
 
Booted into windows now and shows 2GB.
 
thanks for your help Quackers, even if it only made me try a few different things. :)

---

### Post by Quackers on 2010-10-13
Sometimes that's all it takes :-)
Enjoy your 2Gig

---

