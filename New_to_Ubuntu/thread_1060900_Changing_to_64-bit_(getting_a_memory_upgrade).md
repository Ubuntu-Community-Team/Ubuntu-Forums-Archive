---
title: "Changing to 64-bit (getting a memory upgrade)"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by steve70 on 2009-02-05
I have a PC that's getting a 4GB memory upgrade. It already has 8.10 32-bit installed, but I realize that I have to change to 64-bit in order to utilize all the memory. Any 'checklist' advice before switching over?

Basic specs:

M'board = EVGA nForce 650i Ultra
CPU = Intel Core 2 Dual (2.2Ghz)
RAM Already installed = 2GB (Total after upgrade = 6GB)

---

### Post by insane_alien on 2009-02-05
checklist,

1/ is everything backed up?
2/ have you burned the 64-bit(AMD64) CD?
3/ do you have a free hour in which to reinstall?
4/ do you have a cuppa to drink while its working its magic?

its not complicated and there are only problems in very rare cases now.

---

### Post by Thelasko on 2009-02-05
> **steve70 said:**
> ...I realize that I have to change to 64-bit in order to utilize all the memory.

You don't *have to* change to 64-bit if you don't want to.  You could enable [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension").  I've never tried PAE, and I don't know how difficult it is to enable.  I'm just saying, 64-bit is not your *only* option.

Also, you may want to try to open synaptic and in the file menu, save your markings.  This way, when you reinstall, you can easily install the programs you had installed before.  I've never done this myself, but it may save you some time.

---

### Post by ptn107 on 2009-02-05
If your '/home' folder is on it's own partition then you might as well install the 64-bit version since your personal stuff is safe.  As always backup your stuff first, though it's gotta be next to impossible to screw up the installation.

---

### Post by dishbert on 2009-02-06
I too will be upgrading to a 64 bit cpu, new motherboard and new RAM.  

Question 1:  is there a way just to "upgrade" my existing 8.04 installation with the 64 bit CD?

Question 2:   Assuming the answer to 1 is "NO", I have everything backed up using Acronis on an external drive, and I can restore individual files and directories that way.  I'd like to that with most everything.  Is this a good idea?  (I have stuff like Mythtv that was compiled on the 32 bit version.)

Question 3:  What directories or files should I leave alone from the 64 bit install?

---

### Post by Thelasko on 2009-02-09
> **dishbert said:**
> I too will be upgrading to a 64 bit cpu, new motherboard and new RAM.  

First off, [here are some FAQs about 64-bit.]("http://ubuntuforums.org/showthread.php?t=765428")

Answer 1: No, you cannot upgrade

Answer 2: I'm not that familiar with Acronis and I also don't know what your settings are.

Answer 3: Leave your /home directory(or partition) alone.  You should reinstall all of your programs so you will have the 64-bit versions.  As I mentioned above, you can save your markings in Synaptic so you can reinstall all of your old programs (hopefully with 64-bit versions) quickly and easily.  This is a new feature and I've never tried it, so use it at your own risk.

---

