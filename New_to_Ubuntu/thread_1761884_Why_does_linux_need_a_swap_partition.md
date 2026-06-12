---
title: "Why does linux need a swap partition ?"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Phil Stone on 2011-05-18
Since starting out with linux I have always accepted that linux requires a swap partition and understood this to be used as a kind of ram space for use in operating the system.

Given that ram sizes are far larger now than when linux was initially concieved, can anyone give a brief view as to why a swap is required, or what its actual purpose is, if my assumption is lacking?

---

### Post by tgm4883 on 2011-05-18
IIRC Hibernate uses the SWAP partition. You actually don't have to have a SWAP partition, but it is recommended in case you do use up that much memory in normal operation.

---

### Post by mick222 on 2011-05-18
As far as i understand there is no real need for a swap partition as long as your system has enough ram to support the applications you run. Most people keep one as it is automatically set up during a guided install.

---

### Post by Phil Stone on 2011-05-18
Ah, ok, 
but what is IIRC hibernate? 
I'm guessing thta's not what you call it when you are ignored in IRC.lol

---

### Post by false truths on 2011-05-18
IIRC=If I Recall Correctly.

Hibernate is when your computer stores all RAM data on the hard drive (in the swap partition) and completely powers off, but instead of starting up next time, it just pulls the data from swap to RAM and resumes your work where you left off.

---

### Post by Phil Stone on 2011-05-18
Great - Thanks Ppl !

---

### Post by Lateralis on 2011-05-18
From memory...  Which isn't too great!  

Swap is really only used when the system begins to run low on unused RAM.  When that occurs, pages in the RAM which are utilised rarely are "swapped" out to the swap partition (or swap file, if you have one of those instead of a dedicated partition) to make room for pages which are more frequently used.  This is important, as access times with RAM is measured in nanoseconds, whilst conventional hard disks, being mechanical beasts, take much longer to read/write (typically on millisecond times cales).  If a page in the swap suddenly starts being used a lot it will be "swapped" back into the physical RAM.  However, this swapping in and out takes time.  If your computer is running very low on available RAM and is swapping pages in and out an awful lot as a result, then your system will begin to noticeably slow down, with installing more RAM being the only remedy.  

Also, the swap is used for dumping the physical memory to disc during hibernation, as power to the RAM chips is switched off.  It is for this reason that people recommend using a swap partition which is, as a rule of thumb, approximately 1.5-2 times larger than the total amount of RAM you have.  

In the past few years, I've noticed that the swap partition is barely used on both my desktop and PC (both with 4 GBs of RAM).  Sometimes the system will utilise the swap whilst still having 30% of my RAM free, but you I don't notice it when it does.  Only once have I had a situation where almost all my RAM and swap was used, but that was due to a buggy program!

---

### Post by madjr on 2011-05-18
> **false truths said:**
> IIRC=If I Recall Correctly.

Hibernate is when your computer stores all RAM data on the hard drive (in the swap partition) and completely powers off, but instead of starting up next time, it just pulls the data from swap to RAM and resumes your work where you left off.

so you will always still need the swap partition to hibernate no matter how much ram?

---

### Post by Lateralis on 2011-05-18
Yes.  In standby/suspend, the RAM is still powered so data is retained within the physical memory.  This does mean that the computer, whilst consuming less power than when fully on, is still consuming power.  In hibernate mode, the power to the RAM is turned off entirely and the computer sits in a state not dissimilar from a computer which has been fully shutdown.  This does mean any data in the RAM needs to be dumped to disc during hibernation otherwise it is lost to the ether.  During wakeup from hibernation, the data in the swap partition is restored to the RAM, restoring the PC to the same state it was in before hibernation.

---

### Post by aysiu on 2011-05-18
> **madjr said:**
> so you will always still need the swap partition to hibernate no matter how much ram?
Hibernate, yes; sleep, no.

I know some people like to hibernate, but I **never** hibernate my computer, so I never have a swap partition. I either put it to sleep (a.k.a., *suspend to RAM*), or I shut it down completely.

---

### Post by SecretCode on 2011-05-18
Strictly, a swap **partition **isn't required at all. For occasional swapping ... the day you need 9GB of virtual memory ... you can swap to a **file **instead of a partition.

With a certain amount of extra setup, you can also enable hibernation to the swap file.

Details in this thread: [[all variants] HOWTO: Use swapfile instead of partition and hibernate - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=1042946)

---

