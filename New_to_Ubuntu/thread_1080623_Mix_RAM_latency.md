---
title: "Mix RAM latency"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by alanwalterthomas on 2009-02-25
I want to know if adding inferior RAM will harm the performance of existing RAM, & how best to configure/install it.

Motherboard: Gigabyte GA-MA780GPM-DS2H (should support up to 16 GB) with Athlon X2 4850e (I plan to get a Phenom II in a year or two.)

I have:
2x1 GB OCZ Platinum XTC DDR2-800 CL4-4-4-15 Rev. 2

I am considering adding:
2x2 GB OCZ Platinum XTC DDR2-800 CL5-5-5-18
because it's just a tad more expensive than 2x1 GB of the Rev. 2 stuff which I bought earlier with a good rebate. I'd use x64 if I got it to use all 6 GB. 

As far as I can tell the only difference in the Rev. 2 version is the better latency.
Can a hardware guru tell me what issues I face if I put in the higher latency RAM?

Sorry to complicate the answer, but I'm trying to understand details even if the difference is a few nanoseconds. I'm also thinking about the following:

My motherboard has 2 channels, 4 sockets for DDR2 RAM. Right now, the 2x1GB Rev. 2 sticks occupy the two sockets (1 & 2) nearest the processor (yellow) while the two furthest (red) are empty. From close (1) to far (4) from the processor, 1 & 3 are on one channel while 2 & 4 are on the other.

I could arrange the RAM in several different ways. The manual says I should try to keep the same type of ram in the same colour socket. Would I be better off putting the Rev. 2 memory farther from the processor & the slightly slower memory closer to compensate? or the other way around? I mean, would that help them work at the same speed, or do I lose the latency of the Rev. 2 memory anyway?

Should I tweak anything in the bios if I mix these two ram types? Special considerations if overclocking? (heard sthg about timing & voltage settings?)

Thanks for the education,

---

### Post by jerrrys on 2009-02-26
when mixing different speeds and latencies, the motherboard will use the lowest speed and the highest (slowest) latencies for all the sticks.
[http://www.devhardware.com/forums/memory-35/can-i-mix-ram-speed-and-latency-102250](http://www.devhardware.com/forums/memory-35/can-i-mix-ram-speed-and-latency-102250).
if your going to OC the FSB in my opinion only the best will due

---

### Post by alanwalterthomas on 2009-06-11
I'd just like to check before I waste money...

Should I expect stability problems if I added 2x2GB OCZ Reaper 4-4-4-15 memory to the 2x1GB Platinum Rev. 2 memory I have now?

What about adding another brand's 4-4-4-15 memory?

I know mixing ram often doesn't work if it's done +- randomly, but how much trouble should one expect if mixing same MHz & latencies?

Thanks,

---

### Post by Gazneth on 2009-06-11
Considering the speed of your current processor why would you need more than 2 GB of memory to use Ubuntu. If you are doing image or video work you get the most bang for the buck with the fastest processor that fits your budget. Unless you use a 64 bit Ubuntu version the OS only picks up a max of 3GB memory. Check to make sure your processor supports a 64 bit OS. 
My system as I am typing this post has running: Firefox 7 tabs open, file transfer 25 GB, Virtualbox winXP pro, and Transmission running, my memory usage is 1.3 GB of 3GB, and 60% processor load on 2 cores. Memory is cheap, but why have more if it's not needed.

---

### Post by alanwalterthomas on 2009-06-11
I'll likely try 64 for 10.04, about the same time I'd get more memory & a new processor. (the one I have works with 64, but I figured I'd give it some more time to become more common/more perfectly supported)

I've never had applications use the full 2 GB, but AFAIK Ubuntu uses extra ram to cache things so that they'll open faster next time they're run.

type free -mt & you'll see what I'm thinking about.


Anyway, any thoughts on mixing different ram of same specs?

---

