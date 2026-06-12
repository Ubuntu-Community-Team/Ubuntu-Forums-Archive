---
title: "64 versus 32 bit OS - Do I Need To Care?"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by tasbury on 2010-06-03
I'm looking at a 64-bit desktop.  It probably won't have more than 4GB of memory.  I'm wondering whether there is a performance advantage to 64-bit versions of the OS and applications over 32-bit counterparts on the same machine.  Is the memory access or integer add time better?  Anything?

---

### Post by lsk3993 on 2010-06-03
> **tasbury said:**
> I'm looking at a 64-bit desktop.  It probably won't have more than 4GB of memory.  I'm wondering whether there is a performance advantage to 64-bit versions of the OS and applications over 32-bit counterparts on the same machine.  Is the memory access or integer add time better?  Anything?
This seems useful: [http://lifehacker.com/5431284/the-lifehacker-guide-to-64+bit-vs-32+bit-operating-systems](http://lifehacker.com/5431284/the-lifehacker-guide-to-64+bit-vs-32+bit-operating-systems)

---

### Post by NightwishFan on 2010-06-03
Performance should be better all around on 64-bit.
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

The desktop is making the switch to 64-bit, there are few reasons to not use it. 32-bit is a fine option though, you will not miss anything using either.

You can install 64-bit optimized flash, there are an ample amount of threads about it on here.

---

### Post by Wiebelhaus on 2010-06-03
Performance is greater BUT the only downside is that flash does not function properly on *Unix 64bit , It works but for instance interacting with flash based websites like Grooveshark you cannot grab and pull the volume control down, now on fully supported 32bit *Buntu's you can. I choose for now to use 32bit but as soon as flash fully supports 64bit *Unix , I'll switch.

Cheers.

---

### Post by NightwishFan on 2010-06-03
As I said, try the native 64-bit plugin. It works fine for me.

---

### Post by bodhi.zazen on 2010-06-03
> **tasbury said:**
> I'm looking at a 64-bit desktop.  It probably won't have more than 4GB of memory.  I'm wondering whether there is a performance advantage to 64-bit versions of the OS and applications over 32-bit counterparts on the same machine.  Is the memory access or integer add time better?  Anything?

Unless you have a good reason not to, I advise you use a 64 bit OS.

You are extremely unlikely to notice a difference in performance.

---

### Post by tasbury on 2010-06-06
My take-away here is that there isn't much difference.  The tuxradar  benchmark was particularly interesting.  It looks like there is some  advantage to raw cpu horsepower in 64-bit mode, and it also seems like  memory usage will be more efficient.  On the other hand, the cpu  performance differential probably won't be noticeable, and I get along  fine in xwindows with less than a gigabyte of ram.  

So, it looks like a question of convenience and stability.

Thank you all, this was very helpful.

---

### Post by Metrop021 on 2010-06-06
yep, i'm running 64 bit on 2 gb of ram and it works great, no complaints. flash also works well for me as well (using 64 bit flash plugin with 64 bit opera)

the grooveshark thing that was mentioned earlier also seems to work fine for me too :$

---

### Post by sdennie on 2010-06-06
As said above, the biggest issue with 64-bit is flash and it can kind of be worked around.  As for performance, you can have a look at what it adds by looking here: [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64).  To sum that up, yes 64-bit is faster if your apps are CPU bound and can make use of the registers.  They will also use more memory as all pointers are now double the size.

bodhi.zazen and I have been in disagreement about this for years but, I actually recommend 32-bit.  However, I say that while writing from a 64-bit install...

---

