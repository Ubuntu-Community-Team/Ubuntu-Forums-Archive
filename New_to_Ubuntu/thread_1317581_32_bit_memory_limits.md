---
title: "32 bit memory limits"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by dndrich on 2009-11-06
Ubuntupals:

Does 32 bit ubuntu use 4 gigs of installed memory, or does it only see 3 gigs?

---

### Post by falconindy on 2009-11-06
With PAE enabled, you can use up to 64gb.

---

### Post by howefield on 2009-11-06
> **falconindy said:**
> With PAE enabled, you can use up to 6gb.

The limit is way more than that for PAE.

---

### Post by dndrich on 2009-11-06
OK, so what is PAE, and how do I enable it?

---

### Post by hal10000 on 2009-11-06
PAE = Physical Address Extension
With PAE you can use up to 64GB.
I guess (but i'm not sure) it's already activated in the default kernel, so buy your 64GB RAM and try out.

---

### Post by 3rdalbum on 2009-11-06
32-bit Ubuntu uses whatevet Ram is available after your internal components have reserved their chunks out of the 4gb address space.

If your CPU is capable of 64-bit, you should use 64-bit Ubuntu. Otherwise, you can install the server kernel to get the aforementioned PAE.

---

### Post by Darce on 2009-11-06
Is the answer to the initial question actually 4Gb minus any other RAM your system accesses ie: Graphics and such.

So if you had 4Gb installed ram and a graphics card with 512Mb, you'd see and be able to use a total 3.5Gb System RAM ?

Cheers,

Tim

---

### Post by SaintDanBert on 2009-11-06
> **hal10000 said:**
> 
PAE = Physical Address Extension
With PAE you can use up to 64GB.
I guess (but i'm not sure) it's already activated in the default kernel, so buy your 64GB RAM and try out.


All of this is likely true. However, each motherboard -- tower, pizza, or laptop -- has mechanical limits to the amount of RAM that actually works. Read the little book that describes your motherboard.

Cheers,
~~~ 0;-Dan

---

### Post by howefield on 2009-11-07
> **Darce said:**
> So if you had 4Gb installed ram and a graphics card with 512Mb, you'd see and be able to use a total 3.5Gb System RAM ?

No, You would start with about 3.2 gig and then the graphics card would take 512 meg from that and leave the rest as usable memory.

Ubuntu versions ip  up to Jaunty required using the server kernel bit to get PAE, although I think I read about Karmic enabling PAE in the 32 bit version, I'll see if I can find the links.

---

### Post by Darce on 2009-11-07
> **howefield said:**
> Ubuntu versions ip  up to Jaunty required using the server kernel bit to get PAE, although I think I read about Karmic enabling PAE in the 32 bit version, I'll see if I can find the links.

Thanks, I'd be interested to find out. Before Upgrading from Vista to Ubuntu  ;) I'd often wished I could up my RAM from 2Gb, but it would have been next to pointless with the 32bit addressing limitation. Now I'm running Ubuntu, I don't think I've EVER seen my memory usage go above 40% !! Which makes me wonder if I can utilise it better by having often used apps preload into memory for faster start up ?!

Cheers,

Tim

---

### Post by Paqman on 2009-11-07
If you're worried about being able to address all your RAM, just don't use the 32-bit version. There's no real reason to be using 32-bit Linux on a 64-bit CPU anyway.

---

### Post by SoupFlies on 2010-07-12
The only reason I don't use the 64-bit version, is due to the fact that I am worried about compatability errors, when I was new to linux, I had used the 64-bit version and now I am unsure whether the problems encountered were 64-bit issues, or just me not knowing how what i was doing issues. =/ and I don't want to have to install linux for a 4th time in the past 5 months ;P

---

