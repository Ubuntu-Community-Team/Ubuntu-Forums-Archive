---
title: "Newbie to the world of Linux"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by jfever311 on 2011-07-02
Hey folks, I am a newbie to Ubuntu. A week ago I installed a Samsung 250gig 7400rpm hard drive in my old HP Compaq CQ60. Being a bare drive, I figured I would give Linux a try. So far, so good. The computer still maintains its original AMD Athlon-X2 64 bit processor, and just 2gigs of RAM. I am thinking about upgrading to twin 2gig memory cards soon though. I tend to have multiple tabs and windows open and running simultaneously, and it seems like adding 2 more gigs of RAM may help the computer keep up with the load. The Ubuntu 11.04 seems to be a cleaner OS than the HP counterparts I am used to. It is a little more complicated, but in a good way.

---

### Post by wildmanne39 on 2011-07-02
> **jfever311 said:**
> Hey folks, I am a newbie to Ubuntu. A week ago I installed a Samsung 250gig 7400rpm hard drive in my old HP Compaq CQ60. Being a bare drive, I figured I would give Linux a try. So far, so good. The computer still maintains its original AMD Athlon-X2 64 bit processor, and just 2gigs of RAM. I am thinking about upgrading to twin 2gig memory cards soon though. I tend to have multiple tabs and windows open and running simultaneously, and it seems like adding 2 more gigs of RAM may help the computer keep up with the load. The Ubuntu 11.04 seems to be a cleaner OS than the HP counterparts I am used to. It is a little more complicated, but in a good way.Hi, I have an hp laptop with the same processor and I added two more gigs of ram to it, it is really nice with the extra ram, but unless you are going to be running heaving memory intensive apps, it is not needed, I did it because I run virtualbox and that takes more memory.

---

### Post by ClientAlive on 2011-07-02
Welcome to Linux and to the forums jfever311. Hope you enjoy Ubuntu. I know I have.

:D

---

### Post by 1clue on 2011-07-02
Going from 2 to 4 on any modern OS is a good idea, if you use a lot of apps.

Memory is cheap right now, I'm contemplating bumping my box to 24g to give my VMs a bit more room.

---

### Post by wolfen69 on 2011-07-02
The best thing to do is open system monitor to see how much RAM you are using when you have multiple tabs open, and an app or 2. If you are not using more than 1gb, I wouldn't worry about getting more.

---

### Post by jfever311 on 2011-07-03
Hmm.... Seems that I do not use as much memory as I thought. Perhaps the most I used last night at one time was not quite 70% of my available RAM. I might still upgrade so that when I do add some wanted apps, I will already have the capacity I need. 

Thanks for the tip about System Monitor. Seems like a nice place you fellas have here.....

---

### Post by ClientAlive on 2011-07-03
> **jfever311 said:**
> Hmm.... Seems that I do not use as much memory as I thought. Perhaps the most I used last night at one time was not quite 70% of my available RAM. I might still upgrade so that when I do add some wanted apps, I will already have the capacity I need. 

Thanks for the tip about System Monitor. Seems like a nice place you fellas have here.....


One thing is that if you want to try out 64 bit computing 4 gig is a recommended minimum. Opinions vary widely about 64 bit computing and I won't even go there. I'm just mentioning that the 4 gig of memory thing is a standard recommendation for that.

---

### Post by 1clue on 2011-07-03
If you're going there then I submit that Intel vs PPC makes a huge difference too.  Really they're all different architectures and you need to make an apples-to-apples comparison.  I assumed you were using Intel-compatible 64-bit, which is what I figured everybody is doing who has recent hardware.

---

### Post by ClientAlive on 2011-07-03
```
@1clue
```


Hey, I read your signature. How did you get 4 drives in there. Is it nas or something? Sorry, I know this is off topic but a new computer build has been on my mind lately and I've got my eye on learning little details like this. Maybe you'd pm me or something?

Thanks

---

### Post by 1clue on 2011-07-03
You can PM me if you want, but basically I bought a case big enough to hold the drives I wanted.  Every time you let somebody else build your box you get at least one nasty surprise, often more.  I've bought Macs without building them myself, but there's no way I would let somebody else build my Linux box.

---

### Post by jfever311 on 2011-07-03
So, Aside from upgrading to 4gigs of RAM, what else would improve my computing experience without dumping too much $$ into a newer laptop? Would upgrading the processor also require upgrading the motherboard and other internals?

---

### Post by ClientAlive on 2011-07-03
> **jfever311 said:**
> 
Would upgrading the processor also require upgrading the motherboard and other internals?


That depends largely on type of socket the new processor is designed for. Your AMD chip is probably a socket 939 and that's what the mobo in your machine will accept.

When it comes to upgrading a guy can easily get carried away. One thing leads to another and another and another. Imho, the chip you have is nothing to shake wink at. If it was me I'd just roll with a little more ram and switch the chip over to 64 bit. That's just me though.

---

### Post by jfever311 on 2011-07-03
Okay, that makes sense. This next one will really blow your mind.... ;) The sticker on my computer says that I have an AMD Athlon-X2 64 processor. Is there some way that I have to switch it over to 64 instead of 32 bit? I know the version of Ubuntu we installed is the 64 bit, if that matters

---

### Post by dFlyer on 2011-07-03
To switch over to 64bit you would have to do a reinstall. Another solution is to install the pae kernel which can handle 4 gig of memory.

---

### Post by ClientAlive on 2011-07-03
> **jfever311 said:**
> Okay, that makes sense. This next one will really blow your mind.... ;) The sticker on my computer says that I have an AMD Athlon-X2 64 processor. Is there some way that I have to switch it over to 64 instead of 32 bit? I know the version of Ubuntu we installed is the 64 bit, if that matters


I have an AMD 64 bit chip too, in this laptop. I've never used it in that mode thought so I can't say. You can google it and prob get some answers. I know I've read before that 4 gig of ram is suggested for running 64 bit but I'm not sure it means you can't run it in 64 bit mode if you don't have that much ram. Again, you'd prob have to do some research. I have a lot of luck with google when I use search terms that are like questions but without the question mark at the end. Sorry I can't be of more help.
-------------------------

Edit:

Since you say you have the 64 bit version of Ubuntu installed now, I'm wondering what mode it's in currently. I don't really know much about 64 bit stuff but it makes me wonder if it's even possible to run a 64 bit application (or o/s) without the chip being in that mode. Wish I knew more about it to tell you. Just a curious thing that came to my mind though.
----------------------------

Edit:

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE) (but I don't think this is the same as switching the chip's mode)
[http://support.amd.com/us/Processor_TechDocs/33425.pdf](http://support.amd.com/us/Processor_TechDocs/33425.pdf)
[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

I may have been mistaken. Perhaps there is no switching to be done. Perhaps one just goes ahead and uses the 64 bit apps. I wouldn't know since I've never really looked into it before about 10 min ago.
----------------

[http://www.cyberciti.biz/tips/how-do-i-find-out-if-my-server-cpu-can-run-a-64-bit-kernel-version-apps-or-not.html](http://www.cyberciti.biz/tips/how-do-i-find-out-if-my-server-cpu-can-run-a-64-bit-kernel-version-apps-or-not.html)

---

### Post by wildmanne39 on 2011-07-04
> **jfever311 said:**
> Okay, that makes sense. This next one will really blow your mind.... ;) The sticker on my computer says that I have an AMD Athlon-X2 64 processor. Is there some way that I have to switch it over to 64 instead of 32 bit? I know the version of Ubuntu we installed is the 64 bit, if that mattersHi, all you have to do is run 64 bit operating system, you do not have to switch anything.

---

### Post by 1clue on 2011-07-04
Wait a minute.

If you're running slow and want to juice things up, then you need to start by testing what you have.  You need to find the bottleneck before you know what to fix.

Start by using utilities that show you how much CPU you're using, how much RAM, how much disk activity you have, how much network bandwidth you're using.  If your system is slow, then something is blocking the rest of the system from doing its job, or you're using antique hardware which is just plain slow.

In my experience it is not worthwhile taking old equipment and trying to speed it up.  Chances are good that something will fail shortly afterward, possibly because of the changes you made.  Also, it's a good chance that hardware components made years apart don't work well together.

The biggest point here is that what is a bottleneck for you probably won't be a bottleneck for me, because chances are I use my equipment differently than you do.

---

### Post by jfever311 on 2011-07-04
10-4 on all comments.

 Honestly, my system is fairly fast for an old beater laptop. I bought my wife a Macbook Pro last year w/ the Intel I5, 500 gig 7400 rpm HD, and 4 gig RAM. Her computer is faster, but not by so much that I would spend _*another*_ $2000 to match her speed.... ;)

Now I need to learn more about the correlation between the data provided on System Monitor. 

Thanks everyone for your input and advice. It is greatly appreciated.

---

### Post by amjjawad on 2011-07-04
Unused RAM is wasted RAM.

I have two P4 PCs, one with 512MB and the other has 2GB of RAM.
With Linux and its amazing Memory Handling, I don't need to upgrade any :)

---

### Post by createdcreature on 2011-07-04
I use Linux with a Pentium 4 3.2GHz HT, and 2GB of RAM, and an NVidia Graphics card.

---

### Post by 1clue on 2011-07-04
> **amjjawad said:**
> Unused RAM is wasted RAM.

I have two P4 PCs, one with 512MB and the other has 2GB of RAM.
With Linux and its amazing Memory Handling, I don't need to upgrade any :)

This is not exactly true for Linux.

Linux uses "unused" RAM as a disk cache.  If I leave my system up for a month, System Monitor shows more and more of it used as cache, and I've had as much as 11G used, in combination of running apps, swap and cache.  The only reason my swap ever shows anything is because I use tmpfs for a lot of my temp storage, which means the temp files are written to RAM instead of to the disk.  The more of the disk you have stored in RAM, the less disk accesses you need to make which makes your system faster.

If you use your system for awhile, eventually it will approach or exceed the speed of the same system with a solid state drive but less RAM.  The SSD will be faster on writes, but the cached system will be faster on reads.  I've found that if you do your homework on proper use of tmpfs, a normal day of using a computer has remarkably few disk accesses.

---

### Post by amjjawad on 2011-07-04
> **1clue said:**
> This is not exactly true for Linux.

Linux uses "unused" RAM as a disk cache.  If I leave my system up for a month, System Monitor shows more and more of it used as cache, and I've had as much as 11G used, in combination of running apps, swap and cache.  The only reason my swap ever shows anything is because I use tmpfs for a lot of my temp storage, which means the temp files are written to RAM instead of to the disk.  The more of the disk you have stored in RAM, the less disk accesses you need to make which makes your system faster.

If you use your system for awhile, eventually it will approach or exceed the speed of the same system with a solid state drive but less RAM.  The SSD will be faster on writes, but the cached system will be faster on reads.  I've found that if you do your homework on proper use of tmpfs, a normal day of using a computer has remarkably few disk accesses.

Perhaps we're talking apples and oranges here :)

If someone is using his machine for Web Browsing, Emails, Music and Word Processing, he/she does NOT need 12GB of RAM no matter what OS he/she is using.
On the other hand, those who are working as Graphics Designers or those who are Games Addicted, they may need a more powerful PC.

In my case, I'm so happy with 512MB on one of my PCs because I know how to use it and I also know what kind of System (OS) and Applications I'm running on.

Linux is using totally different approach than Windows when it comes to Memory Handling ;)

---

### Post by 1clue on 2011-07-04
You're right, but you're also not right.  It has everything to do with what you're using the computer for, and not so much to do with "knowing how to use it."

You're right that no normal user needs 12G RAM or an i7.  Or a $300 USD sound card, or a fancy video card, or RAID, or any number of other things I have going on.

What I'm saying is that if your system hits swap AT ALL for the traditional use of swap, then you CAN USE more RAM.  IMO you should never, ever swap RAM to disk unless you're doing something extraordinary.  If you have no tmpfs mounts on your system, your swap should be zero, always.

Consider that 4G sticks of ddr3 laptop memory are $40 each right now, and ask yourself if you can't afford two of them in the interest of battery life if nothing else?  Memory is really cheap right now, and the cheapest, easiest way to make sure your system is running nicely.

---

### Post by amjjawad on 2011-07-04
> **1clue said:**
> You're right, but you're also not right.  It has everything to do with what you're using the computer for, and not so much to do with "knowing how to use it."

You're right that no normal user needs 12G RAM or an i7.  Or a $300 USD sound card, or a fancy video card, or RAID, or any number of other things I have going on.

What I'm saying is that if your system hits swap AT ALL for the traditional use of swap, then you CAN USE more RAM.  IMO you should never, ever swap RAM to disk unless you're doing something extraordinary.  If you have no tmpfs mounts on your system, your swap should be zero, always.

Consider that 4G sticks of ddr3 laptop memory are $40 each right now, and ask yourself if you can't afford two of them in the interest of battery life if nothing else?  Memory is really cheap right now, and the cheapest, easiest way to make sure your system is running nicely.

I tend to agree with you but also disagree at some point. Two approaches but we both are using Linux and that what does matter :)

It's always good to discuss these things, that's one of the reason why I'm here but of course I can't make everyone thinks my way :D

I know Hardware these days is much cheaper than 10 years and much much cheaper than 20 years ago. I remember laptops were around 2000-3000$ 5 years ago (I guess) while now, with 1000$ or less, I can get more than what I really need. Quality vs Quantity vs Price and it's another story I don't prefer to discuss here :)

Attached is a screenshot for Ubuntu 11.04 Classic Desktop with no effect on P4 @3GHz and less than 512MB of RAM. I'm also using old IDE HDD. It's probably a basic machine that I don't do much with it.
I also don't expect much. My other PC is also P4 but with 2GB RAM.
I set swap to be 2GB just in case. I know I don't need that much but again, just in case.
I'm using this PC for testing purposes. 
My other PC with 2GB RAM is kind of idle ... I'm not using it anymore.

My whole point was from the beginning is: 
> **Unused RAM is wasted RAM**.

[I]I read that in Linux Arch's Website. They have a very interested philosophy. 
[/I]Point is: There are lots of users who freak out when they find out that their OS has taken all the available physical RAM they have and think to upgrade just because of that. IMHO, this is not right even though RAM is cheap nowadays. I hope you got my point.
If I ever want to use 12GB of RAM, then I must be sure that I'll use it all. Not just use 4GB and leave 8GB unused. This is totally a waste ;)

Again, two different approaches but we're on the same page which is Linux :)

---

### Post by 1clue on 2011-07-04
> **amjjawad said:**
> I tend to agree with you but also disagree at some point. Two approaches but we both are using Linux and that what does matter :)

It's always good to discuss these things, that's one of the reason why I'm here but of course I can't make everyone thinks my way :D


Absolutely correct, only in my case I don't even WANT everyone to think my way.  Diversity is what makes the world go around.

> 
I know Hardware these days is much cheaper than 10 years and much much cheaper than 20 years ago. I remember laptops were around 2000-3000$ 5 years ago (I guess) while now, with 1000$ or less, I can get more than what I really need. Quality vs Quantity vs Price and it's another story I don't prefer to discuss here :)


At my company, we recently put together a 6-core AMD box with 16G RAM for $800.  It's a screamer, to be used to test server software, even though it's using desktop hardware.  My opinion about reusing old hardware was pretty dim even before that, but now there's almost no reason why I would attempt it.  Right now it's just too cheap to make it all from scratch to make it worth bothering with old hardware, and you get much much better performance.

In my case I'm developing server software and using one or more virtual machines on a regular basis.  I actually have a use for the RAM, but even when I wasn't using any VMs my system would eventually cache a massive amount of stuff from the disk, and I could tell it was getting noticeably faster.



> 
Attached is a screenshot for Ubuntu 11.04 Classic Desktop with no effect on P4 @3GHz and less than 512MB of RAM. I'm also using old IDE HDD. It's probably a basic machine that I don't do much with it.
I also don't expect much. My other PC is also P4 but with 2GB RAM.
I set swap to be 2GB just in case. I know I don't need that much but again, just in case.
I'm using this PC for testing purposes. 
My other PC with 2GB RAM is kind of idle ... I'm not using it anymore.

My whole point was from the beginning is: 

[I]I read that in Linux Arch's Website. They have a very interested philosophy. 
[/I]Point is: There are lots of users who freak out when they find out that their OS has taken all the available physical RAM they have and think to upgrade just because of that. IMHO, this is not right even though RAM is cheap nowadays. I hope you got my point.
If I ever want to use 12GB of RAM, then I must be sure that I'll use it all. Not just use 4GB and leave 8GB unused. This is totally a waste ;)

Again, two different approaches but we're on the same page which is Linux :)

---

### Post by amjjawad on 2011-07-05
> **1clue said:**
> Absolutely correct, only in my case I don't even WANT everyone to think my way.  Diversity is what makes the world go around.

Couldn't agree more :)

---

