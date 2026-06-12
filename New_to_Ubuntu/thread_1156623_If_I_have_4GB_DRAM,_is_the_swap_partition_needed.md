---
title: "If I have 4GB DRAM, is the swap partition needed?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by ladasky on 2009-05-11
Not that anyone needs to be stingy with hard disk space these days, but...
 
I run some pretty intensive computations and have occasionally managed to fill my physical RAM.  This results in a lot of disk swaps, and performance degradation.  My current system has 1 GB of DRAM.  I am considering upgrading to 4 GB.
 
Now, that would be the full 32-bit address space, covered by physical RAM.  In that case, does the swap partition serve any purpose?  It's my understanding -- I could be wrong -- that the data in the swap is mapped using the same address space as system memory.

No, I don't think I need to go to 64-bit addressing just yet.  Some of the applications I use are not well-supported in the 64-bit environment anyway.

Thanks for your wisdom!

---

### Post by collinp on 2009-05-11
Even with 4GBs of RAM, you can still fill it and have to use your swap. So yes, you will still need it.

---

### Post by Locutus_of_Borg on 2009-05-11
swap is not used only when you run out of ram space

id advise at least 2 or so gigabytes of swap space, I use 4

---

### Post by TheNosh on 2009-05-11
you don't _need_ a swap partition in any case to the best of my knowlege, but it is strongly advised. personally i have 4 primary partitions (two for windows, two for linux) without a swap partition so i don't have one, but i would if i hadn't reached the primary partition limit (though so far i've had no problems)

---

### Post by Redache on 2009-05-11
> swap is not used only when you run out of ram space

id advise at least 2 or so gigabytes of swap space, I use 4 	

Typically anything above 2Gb is a waste as the speed decrease would become extremely invasive for any user. 

Swap on Linux is usually only used when there's no Physical Ram Left, I've never actually seen my install use the Swap (Could do it when I'm not looking though).

32-Bit won't give you all 4Gb, normally you'd see about 3-3.2 as the address space also includes any other components that have ram on board (think Graphics Cards). 

3gb would probably be better as then you're not losing close to a gig. Or go for 4 Gb and use a 64-Bit OS.

---

### Post by Locutus_of_Borg on 2009-05-11
> **Redache said:**
> Typically anything above 2Gb is a waste as the speed decrease would become extremely invasive for any user. 

Swap on Linux is usually only used when there's no Physical Ram Left, I've never actually seen my install use the Swap (Could do it when I'm not looking though).

32-Bit won't give you all 4Gb, normally you'd see about 3-3.2 as the address space also includes any other components that have ram on board (think Graphics Cards). 

3gb would probably be better as then you're not losing close to a gig. Or go for 4 Gb and use a 64-Bit OS.
i went with 4gb as i like to use suspend which writes to swap, if the documentation is correct, and did not want to have any worry over not having enough.

using a 32bit OS here and recognizing 3914MB of my 4096MB of ram

---

### Post by tkelito on 2009-05-11
It may "see" it but it cannot utilize more than what is previously stated.  It is the limitations of a 32-bit OS.  At the cost of RAM now a days, what is difference between 3 or 4 anyways... not much.  I personally by default always setup a swap as double the ram but this discussion is almost as frivolous as talking about using a Windows Pagefile.  Which in my eyes only serves one purpose, to record any crash dumps if the machine BSOD's.

-tkelito

---

### Post by Ericyzfr1 on 2009-05-11
Do Back-up applications like G4l or Clonezilla use the swap space? In the past I noticed an increase in performance with a larger swap partition, it may not be related.

---

### Post by jaithehulk on 2009-05-12
Swap above 1.5gigs is a waste....so continue using swap memory size of only 1-1.5gigs..in your case with a 4gb RAM swap shld not be needed.

---

### Post by Locutus_of_Borg on 2009-05-12
> **tkelito said:**
> It may "see" it but it cannot utilize more than what is previously stated.  It is the limitations of a 32-bit OS.  At the cost of RAM now a days, what is difference between 3 or 4 anyways... not much.  I personally by default always setup a swap as double the ram but this discussion is almost as frivolous as talking about using a Windows Pagefile.  Which in my eyes only serves one purpose, to record any crash dumps if the machine BSOD's.

-tkelito
no, it can utilize all 4 gb of ram
physical address extension allows the kernel to use up to 64 gb

---

### Post by djuke04 on 2009-05-12
> **jaithehulk said:**
> Swap above 1.5gigs is a waste....so continue using swap memory size of only 1-1.5gigs..in your case with a 4gb RAM swap shld not be needed.

How do you adjust swap size? I do not recall setting the size during setup and system monitor claims I have 11.2 Gb of swap, not that I've ever used more than 7% that I can remember seeing.  

Will this hinder performance or just be inconsequential? 

I couldn't give a crap about the space if that's all it affects, I've got more space on my hard drives than I could ever know what to do with or actually need.

Thanks!

---

### Post by swoody on 2009-05-12
ladasky - If you're filling up your RAM now, it may be a smart idea to include a swap partion even after upgrading to 4gigs. You may not fill all you RAM, but then again, maybe you will? If you use the 'Hibernate' option on your computer, your swap will have to be equal or larger than your RAM - so at least 4GB. I always prefer to play on the safe side of things. However, if you'd like to make sure that you get the best performance from your computer, and it only uses the swap partition when your RAM is nearly full, you may want to consider changing your swappiness value. There's a nice guide on what swappiness is, and how to change it here:
[https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27](https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27)
With 4 gigs, you're probably not going to need swap all that much, so I would consider lowering it to a value of 10.


djuke04 - Having a large swap partition is not going to inhibit your performance in any way. Making it smaller will not net you any performance gains. If you would like to make your swap partition smaller, the best way to do it would be to use gparted from a LiveCD.

---

### Post by waspbr on 2009-05-12
Depending on what you use you computer for , then you may need a big swap. I have 8Gb of RAM but due to some computational programs that I run, I need at least 16Gb of swap... 

tho for regular computer use, I would suggest a swap the same size as your RAM

---

### Post by Sef on 2009-05-12
Swap is needed for suspend and hibernation.

---

### Post by SlonUA on 2009-05-29
> **ladasky said:**
> Not that anyone needs to be stingy with hard disk space these days, but...
 
I run some pretty intensive computations and have occasionally managed to fill my physical RAM.  This results in a lot of disk swaps, and performance degradation.  My current system has 1 GB of DRAM.  I am considering upgrading to 4 GB.
 
Now, that would be the full 32-bit address space, covered by physical RAM.  In that case, does the swap partition serve any purpose?  It's my understanding -- I could be wrong -- that the data in the swap is mapped using the same address space as system memory.

No, I don't think I need to go to 64-bit addressing just yet.  Some of the applications I use are not well-supported in the 64-bit environment anyway.

Thanks for your wisdom!

Just install linux-server and U will see Ur 4GB. Selecting relative choice by this kernel on Grub boot menu =)
sudo apt-get install linux-server

Keep in mind, that U will have the same Ubuntu Desktop and Full Gaming =)
Yup, swap isn't necessary started from 2GB. Only in fact of using VERY specific software.
So, U always can create swap using just file .. no necessary partition =)

[http://ubuntuforums.org/showthread.php?p=7369718](http://ubuntuforums.org/showthread.php?p=7369718)

---

