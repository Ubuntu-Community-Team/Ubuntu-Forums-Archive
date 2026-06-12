---
title: "is this true??????"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by bhuvarahans on 2010-01-03
i just found this thread on one of the online forums for linux
 
People are offering a list of solutions to this Ubuntu 9.10 problem without checking to see if Ubuntu itself has a problem. I believe this current distribution has a bug that needs fixing. I had the same problem on my laptop and was going to buy a new hard drive, but I removed 9.10 and reinstalled 9.04 and the problem was gone. The problem is with Ubuntu, not your hard drives. 
 
please enlighten as i am facing the same problem of bad sectors with my pc tooo!!!

---

### Post by Methuselah on 2010-01-03
Which problem?

---

### Post by YosefKaro on 2010-01-03
You can install a program with Synaptic called GSmartControl and use it to double check your hard drive.  After it is installed, run it from terminal: gksudo gsmartcontrol  It will tell you if your hard drive passes or not.

-Yos

---

### Post by bhuvarahans on 2010-01-03
well the problem is that linux says my hdd has bad sectors  that it is failing. n then after a few mins it just stops responding.
 
there r no hitches in the installation n also fsck did not turn up ne bad sectors!!!!

---

### Post by 3rdalbum on 2010-01-03
Then you might have bad RAM.

---

### Post by bhuvarahans on 2010-01-03
> **3rdalbum said:**
> Then you might have bad RAM.
 
I am running Windows 7 on the same system.  It is working perfectly.  I even tried check disk and the hard disk is working fine.
 
I tried a dual boot with Unbuntu 9.10 over Windows 7.  It showed the same error "one of your disk is failing. Please check".  I thought it might be an error because of two OS on one hard disk.  
 
Therefore, I removed windows 7 completely by creating partitions afresh and installed Ubuntu 9.10 alone.  I even checked the integrity of the disk before installing the Ubuntu OS.  The entire installation was smooth.  After I restart, it shows "one of your hard disk is failing" and starts hanging after 2 or 3 mins.
 
I have now reinstalled windows7 again and is working absolutely fine.  What should I do to overcome this problem and start using Ubuntu.  Kindly give me step-by-step guidelines/ instructions as am a total newbie to LINUX or UBUNTU
 
Thanks in advance.

---

### Post by DannStarr on 2010-01-03
When you installed ubuntu, did you do a guided partition, or did you manually specify your partitions?

---

### Post by Methuselah on 2010-01-03
Your symptoms are strange.
If you want to test for bad RAM boot from the Ubuntu CD and choose the test memory option when the menu comes up.
It will take a while to complete 1 pass and you will not be able to use windows or Ubuntu while it is running (but you can stop it at any time).

---

### Post by bhuvarahans on 2010-01-03
I tried both partioning manual n guided but same end result
 
also the memory test dind show any errors either

---

### Post by CaptainMark on 2010-01-03
If its during install the most common problem is a bad .iso have you run a md5sum on the install disks iso file? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by k3lt01 on 2010-01-03
> **Methuselah said:**
> Your symptoms are strange.Not really, I had the same thing happen when I first started using Karmic but it only happened on Alpha 4, Beta and RC versions. My guess at the moment is that the OP is using a pre-release version of Karmic.

---

### Post by WhiteHorse on 2010-01-03
Run the disk self-check on the liveCD. If the CD is OK, then you may have a problem with your disk BIOS reporting an incorrect version or possibly you need to enter a wait command to allow the disk to spin-up before being accessible.

Can you tell us the disk model/make? Bios version?

---

### Post by bhuvarahans on 2010-01-03
My HDD is Seagate ST3160211AS ATA device. How do I get the BIOS version without rebooting ?

---

### Post by audiomick on 2010-01-03
> **WhiteHorse said:**
> ...or possibly you need to enter a wait command to allow the disk to spin-up before being accessible.

What helped me in this respect was simply turning off all the fast boot options in BIOS. My HDDs are Samsung, and obviously not the bargain they seemed to be...

---

### Post by TBABill on 2010-01-03
Easiest is to just ignore the warning. It's peculiar to Karmic and already reported as a bug. Karmic works fine, as does the HD, even with the error.

---

### Post by candtalan on 2010-01-03
I saw this problem first only on a pre release version of karmic. However, it was on an old  HD and the errors it reported were probably true, although not show stoppers.

The full release karmic did not show the errors. I also installed karmic onto another old HD which went well. I congratulated myself on the recycling of a 20 GB hd I had rescued. 

A few weeks later, the karmic HD error appeared. This time it was perfecty accurate, the HD had in fact failed, and for example, live CDs Ubuntu nor partition magic would not mount it etc etc.

---

