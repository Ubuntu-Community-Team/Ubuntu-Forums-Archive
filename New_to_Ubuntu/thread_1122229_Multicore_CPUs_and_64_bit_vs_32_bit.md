---
title: "Multicore CPUs and 64 bit vs 32 bit"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-04-10
Okay, there's two points to this thread:

1. What's your take on multiple cores for a CPU? 

I'm planning on building a computer this year and I'm having a hard time deciding between a top of the line dual core, or a mid-range quad core. I know applications have to be programmed to utilize the quad core processor for you to see a huge improvement, so I'm starting to wonder how much of an improvement a person would see without programs that are optimized for quad cores.


2. 64 bit vs. 32 bit OS

What's your take on 64 bit OSs? Is it worth the increase in performance by using a 64 bit OS? I know 32 bit OSs will only recognize 4GB of RAM (I doubt I'll go any higher than 4GB in my build). Is it much more difficult to find 64 bit apps or working with 32 bit apps on a 64 bit OS?

---

### Post by Joeb454 on 2009-04-10
I'm not sure about the first one, I can say with my desktop I opted for the e8400 core 2 duo. It's a 3.0Ghz dual core, and I love it, it's plenty quick enough for me.

As for the 2nd, if you get 4GB RAM, I would totally recommend 64 bit, I'm running it, and have been for a while now, with no issues whatsoever, the availability of software isn't really an issue any longer :)

---

### Post by Lazy-buntu on 2009-04-10
> **Joeb454 said:**
> I'm not sure about the first one, I can say with my desktop I opted for the e8400 core 2 duo. It's a 3.0Ghz dual core, and I love it, it's plenty quick enough for me.

As for the 2nd, if you get 4GB RAM, I would totally recommend 64 bit, I'm running it, and have been for a while now, with no issues whatsoever, the availability of software isn't really an issue any longer :)

So all the horror stories I remember about taking the time to find a 64 bit alternative are over now? :guitar:

---

### Post by Joeb454 on 2009-04-10
I'd say they are. I've not had any issues with flash or java (I just installed ubuntu-restricted-extras and they worked).

Also with Adobe now having released an alpha Flash plugin for native 64 bit support, things are still looking up :)

---

### Post by mp035 on 2009-04-10
Agreed, I have had 2 64 bit systems, 1 intel, and 1 amd when I first switched to a 64bit OS, support was a problem, but with the advent of such great tools as getlibs, you can run 32 bit apps on a 64 bit OS, you don't even need to know what 32 bit libraries you need, getlibs will figure it out from the executable!

Flash player though, it's the one thing I still can't get working reliably.

---

### Post by Lazy-buntu on 2009-04-10
For those who say 64 bit, how's the improvement in performance over 32 bit? It sounds like it's worth the switch if you've got the hardware to support it already?

---

### Post by mp035 on 2009-04-10
Bingo.  If you've got the hardware, use it.  But if you're running a 32 bit CPU already, it's probably not worth the change.  The only heavy utilization of 64 bit calculations is in pointer dereferencing for memory over 4GB. A 32 bit CPU can natively handle integers up to 4.2 billion, so there are not many real world calculations that require more than that.

---

### Post by Lazy-buntu on 2009-04-10
I'll start looking for a CPU guide of some sort. I really want to balance cost and performance when I build my PC later in the year, but I don't want it horribly outdated by the end of 2010.

I'd like to find out how each of the specs determine how well a CPU performs. I.E. how much does L1/L2/L3 cache, clock speed, manufacturing tech, number of cores, hypertransports, etc. affect the performance of a CPU.

Like given these four CPUS, using no overclocking, and using the same mobo:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103300](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103300)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103773](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103773)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103249](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103249)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103471](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103471)


What's your best bet with about a 600-750 budget build (excluding monitor)?

---

### Post by Lazy-buntu on 2009-04-10
This was probably the best resource I came across: [http://en.wikibooks.org/wiki/How_To_Assemble_A_Desktop_PC/Choosing_the_parts/CPU](http://en.wikibooks.org/wiki/How_To_Assemble_A_Desktop_PC/Choosing_the_parts/CPU)

However, it doesn't really go into specifics about how to gauge the importance of cache and FSB speed compared to raw clock speed.

edit: pretty good thread on 32 bit vs 64 bit [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by dot2kode on 2009-04-10
My laptop I'm on has an Intel Core 2 Duo T5800 (2GHZ each core) and I love it...I didnt jump up to the 4 gigs of ram though I stayed at 3 for now but the option is there to add it, so far I see no need to I can run HD (720 and 1080) on this sucker just fine even out to my TV from an HDMI plug...Gota love Ubuntu ;P

---

### Post by SuperSonic4 on 2009-04-10
The more the merrier of course :p

but a dual-core is satisfactory for my needs

---

### Post by Lazy-buntu on 2009-04-10
I've found some good info on 64 bit vs 32 bit. I think I'll take the plunge with Jaunty. I'll go right ahead with a fresh install of 64 bit and ext4.

The only thing I'll have to remember is to write down or bookmark all the things I need to do after I install though lol.


Anyway, I'm still thinking about the dual vs quad core situation. On one hand, I don't want my first PC build to be outdated from day one. On the other hand, if quad cores aren't worth an extra 100+ dollars over a nice dual core, I don't have that kind of money to waste if I'm not going to see a difference. Quad cores, I'd have to guess, probably show a considerable improvement in media encoding.


Either way, how do you choose your CPU? How do you look at clock speed, L1/L2/L3 cache, frontside bus speed + Hyper Transports, etc. [you could include how you would pick an intel and how you would pick an AMD if you want]

---

### Post by Marko723 on 2009-04-10
I just bit the bullet and ordered the hardware to build a Ubuntu machine. I know it's not a power house, but it was a price I can live with, and my wife won't be too upset with.   I'd like to hear more about the positive benefits of installing 64-bit vs. 32-bit.

This new machine will be maxed out at 4GB due to motherboard limitations, Intel E5200, and a 7300GT video card.  

Is 64-bit still a good choice, or should I stick with 32-bit?  

Sorry if I'm posting this in the wrong thread, I'm new here and this is my 1st post.

Mark

---

### Post by Lazy-buntu on 2009-04-10
> **Marko723 said:**
> I just bit the bullet and ordered the hardware to build a Ubuntu machine. I know it's not a power house, but it was a price I can live with, and my wife won't be too upset with.   I'd like to hear more about the positive benefits of installing 64-bit vs. 32-bit.

This new machine will be maxed out at 4GB due to motherboard limitations, Intel E5200, and a 7300GT video card.  

Is 64-bit still a good choice, or should I stick with 32-bit?  

Sorry if I'm posting this in the wrong thread, I'm new here and this is my 1st post.

Mark

No problem, welcome to the ubuntu forums :guitar:

This thread was really helpful for me when I was deciding today: [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by Marko723 on 2009-04-11
> **Lazy-buntu said:**
> 

This thread was really helpful for me when I was deciding today: [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

Thanks!  It looks like a good thread, although it does seem a bit dated. :grin:  I'm currently limited to 4GB of memory, so 32-bit may be my best choice.

---

