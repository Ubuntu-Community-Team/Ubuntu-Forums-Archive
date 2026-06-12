---
title: "Effectively use 8GB RAM"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by skymera on 2009-03-04
I'll be buying another 4GB RAM soon to make a total of 8GB

I want to know if my Ubuntu can effectively use all of it.
Is there a way that i can tell it to cache EVERYTHING in RAM?
Or cache all programs?

I have Preload but it seems to suck.

My total install is 1,8GB

---

### Post by issih on 2009-03-04
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

Generally I'd have thought it was time to start looking at 64 bit, but you can get round it.

As for caching, I don't know of the top of my head, although I suspect there is a way

---

### Post by skymera on 2009-03-04
I already run 64bit :) So no upgrades needed :D

ty for link

---

### Post by albandy on 2009-03-04
it not depends directly on running 64 or 32 bit versions, usually in 64 bit is enabled but you can use more than 4GB in 32 bit versions, also in ubuntu server is enabled by default in 32 and 64 bit

Simply see if your kernel support it:
cat /boot/config-2.6.27-11-generic  | grep HIGHMEM64G 
and if HIGHMEM64G is set to yes

if is set to yes you have high memory support
else you simply need to recompile your kernel enabling this option

---

### Post by skymera on 2009-03-04
Yes i do run 64bit so it's definately supported.

What i want to know is if Ubuntu can cache it all rather than letting it sit there, wasting away

---

### Post by albandy on 2009-03-04
I'm using ubuntu server with 8 cores and 32GB of ram, and 16 virtual machines running, and it uses all the available memory.

---

### Post by skymera on 2009-03-04
> **albandy said:**
> I'm using ubuntu server with 8 cores and 32GB of ram, and 16 virtual machines running, and it uses all the available memory.

Nice.
However, this is a home PC and will be running Firefox, Pidgin and Banshee.

Not 16 virtual machines

---

### Post by mcduck on 2009-03-04
> **skymera said:**
> Yes i do run 64bit so it's definately supported.

What i want to know is if Ubuntu can cache it all rather than letting it sit there, wasting away

That's what it's supposed to do by default.. ;)

But you can't cache data before you access it, so your cache won't fill the whole 8GB until u´you have actually used 8GB worth of data.

Many programs include their own settings for how much RAM they are allowed to use, for example you can increase this in Firefox to keep more of it's cache in memory. But in the end you still need to access all that data before it can be cached..

Preloading allows you to load applications to RAM beforehands but the downside is that it slows your boot time and you probably don't want to slow your boot by pausing to read 8GB worth of program files into RAM..

Anyway, if your Ubuntu install is 1,8GB what would you expect it to fill the RAM with? ;)

Actually it just sounds like you have much more RAM than you are really needing. Load a virtual machine or couple and you'll sure be able to get rid of the annoying free RAM.. :D

---

### Post by marco123 on 2009-03-04
> **skymera said:**
> Nice.
However, this is a home PC and will be running Firefox, Pidgin and Banshee.

Not 16 virtual machines

Why do you "need" 8GB of RAM then?  I have 4GB and even running virtual machines I find this enough.:)

Cheers, Marco.

---

### Post by skymera on 2009-03-04
I play games in Windows.

Plug 4GB XMS2 800MHz is only £34 :)

---

### Post by marco123 on 2009-03-04
Do you mean you want to setup a RAM disk? [http://seobm.blogspot.com/2007/11/howto-make-ramdisk-in-ubuntu.html](http://seobm.blogspot.com/2007/11/howto-make-ramdisk-in-ubuntu.html)

---

### Post by Thelasko on 2009-03-04
> **skymera said:**
> I play games in Windows.

Plug 4GB XMS2 800MHz is only £34 :)

You do know that [many versions of Windows only support 4GB]("http://en.wikipedia.org/wiki/Physical_Address_Extension#Microsoft_Windows"), right?

---

### Post by mikechant on 2009-03-04
> You do know that most versions of Windows only support 4GB, right?

And in practice, only 2.5-3.5Gb is actually usuable in 32-bit windows due to the way memory space is mapped.
 
But surely if the original poster knows to run 64-bit Ubuntu then they must be running 64-bit Windows or intending to run it when they upgrade to 8Gb?
I guess cutting-edge games are the most likely applications to run correctly with and make use of the extra memory in 64-bit windows.

---

### Post by unlotto on 2009-05-01
Preload can be configured to be much more aggressive. Although I don't know how well it translate to making use of 8gb ram. I've also seen various posts on mounting /usr/lib or /usr to a tmpfs, which supposedly should give insane speedups. Sadly I have no links. That is what i'm going to look into once I get my ram.

---

### Post by skymera on 2009-05-02
> **Thelasko said:**
> You do know that [many versions of Windows only support 4GB]("http://en.wikipedia.org/wiki/Physical_Address_Extension#Microsoft_Windows"), right?

You know, there has been a 64bit Windows now for a long time.

---

### Post by -kg- on 2009-05-02
The flat fact is, if you want to use anywhere *near* 8GB of RAM, you're going to have to figure out some configuration of running software that uses it.  Otherwise, cheap as it is, the only thing you will have bought with your money is impressive hardware statistics.

Set up some virtual machines; run BOINC distributed computing projects completely from a RAM disk; run some other software from a RAM disk; find other ways to use the memory.  Running software from a RAM disk will speed it up compared to running from disk and use RAM.

There are ways to use it, and as for it slowing down boot time, so what?  I rarely reboot my computers anyway, and the time it saves more than makes up for any boot time increases over the long run.

---

