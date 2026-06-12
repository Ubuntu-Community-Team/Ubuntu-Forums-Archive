---
title: "Install Ubuntu 32 bit or 64 bit?"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-22
Is now a good time to try out 64 bit Ubuntu? 
What are the possible issues? Are flash, Java plugins out? Will apps break down?

Also the benchmarks in the link below do not seem so flattering to 64 bit, I expected a larger improvement. Am I reading the results wrong?

[http://www.tuxradar.com/node/33](http://www.tuxradar.com/node/33)

Thanks a lot

---

### Post by trivialpackets on 2009-05-22
I'm running 64 bit and it's fine for me.  YMMV.  Lots of stickies about this topic in the [x86 64-bit Users]("http://ubuntuforums.org/forumdisplay.php?f=343") forum.

---

### Post by 73ckn797 on 2009-05-22
64 runs fine for me with 6GiB memory. I think that if you have 3Gib or less that you will not see much improvement since 64 uses more memory. That has been the case with me before the jump from 4 to 6GiB.

Java and Flash work just fine. If you install it look for "sun-java6" and "flash-installer" in Synaptic.

---

### Post by Andy06 on 2009-05-22
Yeah I have a sort of noobish question that which embarrassed me when someone asked because I consider myself at least a power user with windows anyway and have tried multiple linux distros.

So here goes:

RAM doesnt actually increase the speed of you apps right? It just allows you to hold more in the fastest form of memory available. So more RAM = smoother faster multitasking. But not necessarily faster single tasking right? For example firefox with 1 GB of RAM never really gets close to eating up the whole 1 GB, so to increase its speed, what should be done? Faster FSB? Faster RAM speed (the 1066 Mhz or whatever) or fast CPU?

Basically what makes the system go FASTER as opposed to just smoother all at once (which is what RAM would do). Should I invest in a better CPU and 64 bit OS for single tasking and moderate multi tasking as opposed to more RAM (which is already 2.5 GB and more than enough, usually only using 10-20%)

Does that even make the slightest sense?:D

---

### Post by AlucardArg on 2009-05-22
It makes total sense. Basically:
The RAM memory is the temporal memory that apps use to work. For example, if you have 1 GB RAM, but a good, fast CPU, you would be able to run few apps, but at a good speed. Now, if you have a huge amount of RAM, you'll be able to open many processes before the computer starts to get sluggish.
The RAM velocity (166, 333, 1066, and so on, Mhz) is the velocity the data stores in the RAM. A bigass RAM capacity, but just 166 Mhz, would be useless, as you would never fill, and use efficiently all your RAM memory.

---

### Post by 73ckn797 on 2009-05-22
If you want more speed in Firefox there are tweaks that do improve the performance. Google for "Firefox tweaks". There are settings that can be changed.

I only see a slight increase in speed using 64bit with the RAM capacity I have.

I was actually surprised how much faster Windows XP runs with "PAE"  (Physical Address Extension) enabled. There is no switch in Ubuntu to enable PAE without recompiling the kernel. The 64bit is enabled by default simply due to being 64bit. Windows really smokes with PAE.

Look at the sticky notes under the 64bit sub-forum. It ought to answer most of your questions. [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by egalvan on 2009-05-23
> **73ckn797 said:**
> 
I was actually surprised how much faster Windows XP runs with "PAE"  (Physical Address Extension) enabled.

So what is the "switch" to make WinXP PAE-enabled?

> 
 There is no switch in Ubuntu to enable PAE without recompiling the kernel.
 The 64bit is enabled by default simply due to being 64bit. Windows really smokes with PAE.


The Server Version of 32bit Ubuntu has the PAE switch enabled, among other differences...

I use 8.04.2 Server Edition with KDE desktop added, to run PAE on a high-RAM machine. Works well.

---

### Post by Andy06 on 2009-05-23
Thanks guys. Helps a lot

I know about the Firefox tweaks, but I was just using it as an example of a large app. Basically what is the best way to increase the speed of apps so that everything opens in a snap, thumbnails get displayed instantly, there is no lag between switching whatsoever. 

What's the best way to do that? Faster speed ram (1066 Mhz, DDR3?), faster FSB, faster CPU with more cores?

As I see it, with windows 7 and Ubuntu 9.04, there is no more point increasing my RAM (which is 2.5 GB DDR2 800Mhzish) and I rarely use even 50% of it. I mostly do moderate single tasking eg: firefox with 10 tabs + maybe one other app at most.

---

### Post by oldos2er on 2009-05-23
A system's speed is always going to be constrained by hard disk I/O, since it is by far the slowest link in the chain. Once you have plenty of RAM and a good CPU, get an hard disk with the quickest I/O access you can find.

---

### Post by gn2 on 2009-05-23
If you do a lot of encoding 64-bit is worthwhile, for audio/video conversion 64 bit will yield BIG performance increases.
For everything else there's no significant difference.

---

### Post by zhhansen on 2009-05-23
I would stick with 32 bit, only for the reason that many of my ubuntu programs only support that architecture. Although 64 bit is growing, most everything is built for 32. 

Thats my 2 cents :p

---

### Post by Andy06 on 2009-05-24
I thought about this issue. Can you elaborate on which major apps are incompatible with 64 bit? I'm assuming the major ones have all been upgraded to handle it, especially the default ones or indeed ones that are default for any major distro (to support the 64 bit on that distro).

Is there a compatibility mode to run 32 bit apps anyway like on windows?

Thanks a lot

---

### Post by bagle on 2009-05-24
well it depends is your prosser a x86-64 or a 64bit one.
x86-64prossesors have x86 or "32 bit emulation while 64 bit amd 64 arcetecture prossers just do 64bit stuff.

    so contenplate that for a while;);):D

---

### Post by Viva on 2009-05-24
64 bit ubuntu works great for me.

---

