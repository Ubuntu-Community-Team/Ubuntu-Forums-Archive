---
title: "More RAM or more CPU ..."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by cwmoser on 2008-12-30
What is better for Ubuntu -- more RAM or more CPU?  Coming from the Windows world,its "BOTH".  Thinking that these beliefs are similar with Ubuntu, I went out and purchased a souped up processor (ADM 64 X2 6000+) and 4GB of RAM (2 x 2GB DDR2).

Here are my observations:

1- I ran System Monitor and started up Evolution, Office Writer, two sessions of NXServer, Crossover/Quicken and vmWare instance running Windows XP.  System Monitor showed that my memory usage was just over 600MB -- and I bought 4GB!!  The Swap file was at 0 bytes.

2- I noted that QuickBooks would not run on my new system.  After removing one of the 2GB RAM strips bringing me down to 2GB, then Crossover/QuickBooks would run.  Hmmm ... can you have "too much memory"?

3- I did note a performance boost with the AMD 64 X2 6000+ versus the Intel P4 3.Ghz cpu.  Not dramatic, but noticeable.  One thing I did observe after I purchase my new CPU and memory and when I opened the case on the Intel PC was that the heat sink was chocked full of dust -- perhaps that was what caused it to sometimes seem to run slow.  A quick clean up with a vacuum cleaner seemed to give my old PC a new life.

So, lets not let our perceptions in the Windows world dictate what we need to do in the Linux world.  From my observations, 2GB of RAM is plenty for Linux - and for some applications (i.e. Crossover/Quickbooks) too much RAM can be bad!!  I think if one wants to spend money on performance, look at getting a faster CPU or a higher performing video card.


Carl

---

### Post by JohnLM_the_Ghost on 2008-12-30
Yeah, it (usually) never hurts upgrading both.
But 4GB RAM for this rig might be a slight overkill.

btw To efficiently use all 4GBs of RAM you should have an 64bit system (one for *x86-64* or *amd64*)

Unfortunately some edges of 64bit OSes haven't been polished...

---

### Post by wizard10000 on 2008-12-30
Here's the short answer  :)

When troubleshooting performance issues the compoment or subsystem that's running at 100% capacity is *always* the bottleneck.  In other words if your CPU is maxed out adding RAM won't help you at all and vice versa.

More CPU and more RAM never hurts but it doesn't always help either - a lot of the time you can realize a better performance gain by optimizing I/O subsystems - namely disk and video.  My desktop PC is an old 2.8GHz single core box with 1GB of RAM, a 10k rpm SCSI boot drive and a SATA data drive - video is an older GF6200 but then I don't do any gaming.  The machine also serves as a myth backend, has apache running for mythweb and even when rendering video never uses more than about 600mb of RAM and 17mb of swap.  Since I/O subsystems are already pretty well optimized if I want the machine to go much faster it's time for a processor upgrade, but this machine's still competent and I expect it will be for another year or so.

---

### Post by ibuclaw on 2008-12-30
More RAM...

The slowest part of any operating system tasks is reading from your hard drive. So it doesn't matter how much RAM you have or what speed your CPU is, if your hard drive is slow, you will have a slow system (in terms of load times).

What the Linux Kernel does to overcome this problem is to utilise the RAM available on your machine, and uses it to cache all data (or most the data) that you run. So if you were to load the same application twice, the second time should be quicker because it is taking most the data files the application uses from RAM, not from the Hard Drive...

My recommendation would be anything from 1GB-2GB... 1GB of RAM and a Single-Core 2GHz processor is more than enough to have a more than usable desktop. (Add a 512MB Graphics card thrown into the mix, and you've got your own hardcore gaming box/visual desktop effects).

So, if you open up system monitor and look at the RAM usage, and find that it is above 75%, don't panic... 50% of the data in RAM is used for cache... it is there to help Linux run quicker :)

Regards
Iain

---

### Post by scorp123 on 2008-12-30
> **JohnLM_the_Ghost said:**
> btw To efficiently use all 4GBs of RAM you should have an 64bit system  .. or use a PAE-enabled 32-bit kernel. ;)

---

### Post by cwmoser on 2009-01-01
I've got 2GB RAM and my swap file never gets used.

I can start up a lot of applications and System Monitor might show that its using 700MB of RAM.

Quite a bit different than Windows :-)

Carl

---

### Post by steveneddy on 2009-01-01
> **JohnLM_the_Ghost said:**
> 

Unfortunately some edges of 64bit OSes haven't been polished...

I find performance in 64 bit Ubuntu to be much better than 32 bit performance on the same laptop.

If you want/need to have and run 4 Gig of RAM then use 64 bit Ubuntu.

Trust me, you will never go back to 32 bit.

---

### Post by JohnLM_the_Ghost on 2009-01-01
> **steveneddy said:**
> I find performance in 64 bit Ubuntu to be much better than 32 bit performance on the same laptop.

If you want/need to have and run 4 Gig of RAM then use 64 bit Ubuntu.

Trust me, you will never go back to 32 bit.
I haven't noticed difference with performance, but then I have not tested it properly.
I'm using 64bit Ubuntu myself. I had some share of bugs and stuff, but nothing major.
I'm quite happy with it!

---

### Post by stderr on 2009-01-02
RAM - For somebody who uses their OS "heavily" (subjective as that term is), I would say 2-4GB is ample. It really does depend what you use it for and what your usage habits are like though. For a more standard user, 1-2GB should be sufficient. For somebody who sits in the terminal almost all the time or doesn't have much open simultaneously, 1GB is likely overkill ;) Critically, if you have enough RAM for day to day operations, buying more RAM won't really improve anything. 

Think of it like temporary work space on your desk. It would be nice to have quite a lot of work area free around you for whatever, but you could have miles of it or metres of it and it won't make much difference to how you use it. The problem comes when you've got so little temporary work space that you're beginning to pile things up around you and it begins to take you ages to find anything. What that point is depends entirely on how much stuff you have on the desk, how much is filed away, etc. RAM is similar. 

And let's not forget the easier solution to low RAM problems: close a few programs down, or with the workspace analogy, file a few things away that you're not using at that point in time. 

CPU - most people don't max their CPUs much at all, aside from gaming. If you do a lot of encoding, decoding, encrypting, ... you could probably use a few more MHz or GHz. But ultimately, it depends again. If your CPU is fast enough to cope with the day-to-day running, then buying a faster CPU will most likely just shave a few seconds off of the occasional decode, or make system boot a sec or so faster. 

For most people, as long as the CPU can handle the regular load, and as long as you're not doing CPU intensive things all the time, a faster CPU won't make that much difference.

Analogy - consider a car. You can have one that does 120mph tops, or one that does 252mph tops. The difference in prices will be huge. However, for day to day trips, dawdling around towns and cities, it won't make the blindest bit of difference. It's only when you get to the long haul motorway trips that you may notice a difference in time taken. Same with CPUs - you can buy a really expensive CPU, but if you don't always "drive at 252mph", i.e. if you don't regularly 100% your CPU (or one of your CPU's cores), then it's neither here nor there which one you have.

HDD - Hard disk speed makes a HUGE difference. If you're running an ancient 5,400rpm hard drive, and you change to a 10,000rpm Raptor, you will notice the difference. 

In terms of data access, HDDs are mechanical devices with moving parts - they're SLOW. VERY slow. Data gets pulled off the HDDs into RAM. RAM is pretty fast in comparison, and is all electronic. Data then gets pulled out of RAM and passed to the CPU, where it's stored in cache memory (L1, L2...). The cache memory is VERY FAST.

So, the more RAM, the more data you can cache in RAM at any given time, so the less you need to get from the slow HDD. But the slow HDD still has to serve the RAM the data. 

Another bottleneck is, of course, the buses on the motherboard that shuttle the data between HDD, RAM and CPU.

But you get the idea; there are many potential bottlenecks. And upgrading something which isn't a bottleneck in your setup won't improve anything much - literally throwing money away.

One added bonus of upgrading the CPU, though, is that you may get more L1 and L2 cache. This is a bonus, because the more data you cache very close to the CPU in incredibly fast memory, the less data you have to wait for from the RAM *and* the HDD. And when we're talking about, say, 90% cache hits on average for the Lx caches, we're talking about some serious time saving. 

So, to conclude (if anyone's still reading - if you are, why, go outside, grab a beer or something :)) faster HDD for your OS would make a reasonably big difference. A CPU with more L1 and L2 cache would make a reasonably big difference. And depending entirely on your setup and your usage patterns, a faster CPU or faster or more RAM may or may not make any real difference.

edit: with regards to 64-bit computing, yes there's a performance benefit, yes it *may* *just* be noticeable, but I'm still not sure it's worth the extra pains that are still involved in 64-bit. Maybe in another half a year or so, when literally everything is released in 32 and 64-bit versions. I first moved to 64-bit many, many years back. I didn't stay there for long :)

edit: I suppose I should mention, a faster CPU will make some things slightly faster (day-to-day). My point is that if you're sitting there with a 5,400rpm HDD, programs will still open slowly. Things may still feel sluggish. 

Also, you do want a bit more RAM than you need for actual programs. If you have the System Monitor applet thing on your panel, you'll likely see that almost all your RAM is in use one way or another. That's good. It's being used as cache, so less has to be pulled from the HDD (i.e., when something's put into RAM, and there's still spare RAM available, why bother removing it when you're done with it? why not leave it there in case you need it again?). 

However, if almost all your RAM is in use for actual programs (open up System Monitor itself, and look under the Resources tab - that's how much actual RAM is NEEDED by programs), then your PC will probably start using your SWAP FILE. You can also see how full your swap file is next to the RAM readout in the Resources tab. If things are put into the swap file,  it means you've run out of RAM and your PC is having to resort to storing temporary data on your really slow (comparatively) hard drive. If it has to keep swapping data between HDD and RAM like that, this will VERY SIGNIFICANTLY slow down your system.

Under Windows, the swap file is almost always in use, unless you tell it NEVER to use the swap file. On a default XP installation, 700MB could be in swap when it's sitting on the desktop doing nowt - that's insane, and slow. On a default Ubuntu install, NO swap space is used unless you're out of RAM. So if System Monitor regularly reports quite a bit of swap file usage and pretty full RAM, then that is a sign that more RAM will definitely equal a decent performance boost.

Or a sign that you've got way too many apps open ;)

---

### Post by egalvan on 2009-01-02
> **stderr said:**
> RAM - For somebody who uses their OS "heavily" (subjective as that term is), I would say 2-4GB is ample.  For a more standard user, 1-2GB should be sufficient. For somebody who sits in the terminal almost all the time or doesn't have much open simultaneously, 1GB is likely overkill ;) Critically,** if you have enough RAM for day to day operations, buying more RAM won't really improve anything**. 

The problem here is that the OP is asking "which is better, RAM or CPU". And we don't know how much RAM he has...which is rather important in order to give a good answer....

If you are running 128MB, then even terminal users will see a speed-up with more RAM. As for a "heavy" user, yes he needs more RAM.

I think 512M is the minimum for a more-modern Linux distro...
I run Puppy 4.12 with 256M, and it runs well... but it's optimized for "smaller" systems.


> And let's not forget the easier solution to low RAM problems: close a few programs down, or with the workspace analogy, file a few things away that you're not using at that point in time. 

Yes, too many people keep too much open all the time... i guess it's a left-over windows habit...


> CPU - most people don't max their CPUs much at all, aside from gaming. If you do a lot of encoding, decoding, encrypting, ... you could probably use a few more MHz or GHz... If your CPU is fast enough to cope with the day-to-day running, then buying a faster CPU will most likely just shave a few seconds off of the occasional decode, or make system boot a sec or so faster. 

Yes.


> For most people, as long as the CPU can handle the regular load, and as long as you're not doing CPU intensive things all the time, a faster CPU won't make that much difference.

Analogy - consider a car. You can have one that does 120mph tops, or one that does 252mph tops. The difference in prices will be huge. However, for day to day trips, dawdling around towns and cities, it won't make the blindest bit of difference. It's only when you get to the long haul motorway trips that you may notice a difference in time taken. Same with CPUs - you can buy a really expensive CPU, but if you don't always "drive at 252mph", i.e. if you don't regularly 100% your CPU (or one of your CPU's cores), then it's neither here nor there which one you have.

Well, I have to say I don't find this analogy apt in this example.

I think you are confusing 'speed' with 'load' when talking about "CPU Load"

CPU 'load' basically tells us how much free time the cpu has.

Another explanation...
'load' is a measure of how many 'free' cycles the cpu has left over.

The faster the cpu finishes its work, the more free time it has.
The more work, the less free time.

"do your chores, then go out and play"

the faster you do your chores, the more time spent playing.
the more chores, the less time spent playing.

speed is how 'fast' you do 'something'
load is how many 'somethings' you are doing per time division

I can't think of an apt analogy...
So here is a TOTALLY INVENTED one....

Three users are applying a filter to a photo, using the gimp...
this filter takes 100 CPU cycles to complete...

user Stodgy has an equally stodgy cpu that does one cycle per second.
so his filter takes **100 seconds to finish,**
and **the load will be 100% for 100 seconds.**

user Zoom has a newer cpu, that does 10 cycles per second,
so his filter takes **10 seconds to finish,**
and **the load will be 100% for 10 seconds.**

user Warp has the latest cpu that does 100 cycles per second,
so his filter **takes 1 second to finish,**
and **the load will be 100% for 1 second.**

notice that the "load" does not change. While the cpu is doing "something", it is busy. So load is 100%
the faster the machine, the less time it took to finish.

The reason your analogy still explains the problem, is that, yes,
the majority of work done on computers is minuscule... so the cpu loafs along, because it doesn't have many 'chores' to do...web surfing, IM'ing, texting, etc are not very heavy chores. So the cpu has more time to 'play'


> 
HDD - Hard disk speed makes a HUGE difference. If you're running an ancient 5,400rpm hard drive, and you change to a 10,000rpm Raptor, you will notice the difference. 


Yes.

> One added bonus of upgrading the CPU, you may get more L1 and L2 cache. ** the more data you cache very close to the CPU in incredibly fast memory, the less data you have to wait for from the RAM *and* the HDD.** And when we're talking about, say, 90% cache hits on average for the Lx caches, we're talking about some serious time saving. 

Yes, and the same reasoning applies to RAM... the more RAM, the faster the data moves...

but it still depends on how much you have already.

I "upgraded" one of my laptops (IBM T40P) from a 1.6GHz PM with 256K cache to a 1.4GHz PM with 2M cache...
yes, it is 'snappier' now, even though technically 'slower'.
And when I upgraded the RAM from 128M to 1Gig, it also had a VERY postive impact on the feel.


> 
So, to conclude (if anyone's still reading - if you are, why, go outside, grab a beer or something :)) faster HDD for your OS would make a reasonably big difference. A CPU with more L1 and L2 cache would make a reasonably big difference. And depending entirely on your setup and your usage patterns, a faster CPU or faster or more RAM may or may not make any real difference.


Again, it depends on where you are starting from....

> edit: with regards to 64-bit computing, yes there's a performance benefit, yes it *may* *just* be noticeable, but I'm still not sure it's worth the extra pains that are still involved in 64-bit. Maybe in another half a year or so, when literally everything is released in 32 and 64-bit versions. I first moved to 64-bit many,** many years back**. I didn't stay there for long :)


Yes, many years back, Linux itself had more problems.
A lot has changed since then...
64Bit has mature tremendously.

---

### Post by stderr on 2009-01-02
> **egalvan said:**
> The problem here is that the OP is asking "which is better, RAM or CPU". And we don't know how much RAM he has...which is rather important in order to give a good answer....

Yes, naturally, I just wanted to give a rough idea to those who are unsure and to emphasize that 4GB is not "necessary", even though RAM prices are cheap now and so many people seem to recommend huge amounts of RAM. People buying new PCs quite often tend to think, well, PCs range from (low end) maybe 1GB to (high end) maybe 4-8GB, so **I suppose I should go for something at least in the middle**, which would be 2-4GB. Which is quite a lot.

> **egalvan said:**
> I think you are confusing 'speed' with 'load' when talking about "CPU Load" [...]
The reason your analogy still explains the problem, is that, yes,
the majority of work done on computers is minuscule..

Quite right; I didn't really attempt to make the distinction in order to keep it simple, and for the reason you give: most of the time it makes no difference. We're talking micro/milliseconds for the *average* user. Because, let's face it, the average user doesn't do much hardcore processing - it's "burst" processing, for short periods of time, not typically occupying even 50% of a core (yes, I know that phrases like "50% of a core" mean very little in reality). 

> **egalvan said:**
> I "upgraded" one of my laptops (IBM T40P) from a 1.6GHz PM with 256K cache to a 1.4GHz PM with 2M cache...
yes, it is 'snappier' now, even though technically 'slower'.

Good term - snappier - that's how I'd describe it. Every time I've upgraded my CPU I've been more concerned about cache than GHz, as you clearly have been too. So, unanimous agreement here - Lx caches (we're typically referring to L2) really do help.

> **egalvan said:**
> And when I upgraded the RAM from 128M to 1Gig, it also had a VERY postive impact on the feel.

I'm sure it did :)

> **egalvan said:**
> 64Bit has mature tremendously.

Yes, I have to admit it has. Almost enough to make the switch. Almost ;)

edit: In fact, I should have mentioned - if all you use a PC for is word processing and the like, what's wrong with a 386? :p I used to work in John Lewis (urgh...) ages ago, and it was always interesting to watch salespersons advising people on PC purchases. It's amazing what high end systems some people would end up walking away with when all they wanted to use it for was to browse the 'net. These are people who had been quite happily stuck on W 3.1 for years and years, and suddenly they're buying some 2GHz 512MB super-system (years back). -sigh-. Still, no doubt it came with the "Vista compatible" sticker hehe ;)

And clearly we're in agreement over this too:

-----------------------------------------------
If you're unsure if a particular upgrade is worth it, post your specs and ask. Likely there'll be someone who's in a very similar hardware boat to you who can give you some indication of what tangible difference, if any, you're likely to perceive.
-----------------------------------------------

---

### Post by ibuclaw on 2009-01-02
> **stderr said:**
> 
Yes, I have to admit it has. Almost enough to make the switch. Almost ;)

What made me switch was the fact that I found out I actually had more control options in the 64bit kernel than what I did in the 32bit one.

ie: 64bit allowed for more acutely tuned power saving on the laptop, whereas 32bit gave almost no cpu options to tweak in the /sys and /proc directories.

I have also recently flashed my BIOS, and was amazed to find that now even more can be done in the 64bit kernel (thank-you Intel/HP). :)


Although, I do have a firm belief that the 2.6.24-ubuntu kernel is one of the most stable/pinnacle kernels of linux. I am intrigued to find hundreds of power saving patches that are in the most recent kernel tree. So what I may end up doing is creating my own patched kernel...

Regards
Iain

---

### Post by egalvan on 2009-01-02
> **stderr said:**
> Yes, naturally, I just wanted to give a rough idea to those who are unsure and to emphasize that **4GB is not "necessary", even though RAM prices are cheap now** and so many people seem to recommend huge amounts of RAM. **I suppose I should go for something at least in the middle**, which would be 2-4GB. Which is quite a lot.



Talk about a hang-over...

Newegg had pairs of 2gig DDR2 sticks at $32, shipped...

so I over-indulged and had one too many...

Now my three high-end machines (dual-core Intel & AMD) are sporting 8gig each...

And my two work machines are maxed (only two slots) at 4gig.

and I have bragging rights.

Ouch, my aching wallet...:)


> So, unanimous agreement here - Lx caches (we're typically referring to L2) really do help.

Absolutely.



> edit: In fact, I should have mentioned - if all you use a PC for is word processing and the like,** what's wrong with a 386?** :p , and it was always interesting to watch salespersons advising people on PC purchases. It's amazing what high end systems some people would end up walking away with when all they wanted to use it for was to browse the 'net. These are people who had been quite happily stuck on W 3.1 for years and years, and suddenly they're buying some 2GHz 512MB super-system (years back). -sigh-. Still, no doubt it came with the "Vista compatible" sticker hehe ;)

And clearly we're in agreement over this too:


Again, absolutely...

The problem with older machines (such as a 386) is finding software that will work, and finding repair parts.

As of four years ago, an older gentleman I knew was still using an old 286 machine, running MS-DOS 5.x, and using a simple text editor to type his business letters. He was very wealthy, and could have purchased a new machine every week... but he was happy with his 'dinosaur'

and yes, I do have "older" machines. But trying to keep them running (the spare-parts problem) means that my oldest is now a Pentium 3 running at 500MHz. But it has 512M RAM stuffed into it.. so it runs rather well... very "snappy", and under Puppy it flies!


And I've now run Vista (Business Premium) for a whole day, with 8gig RAM, Core 2 duo @ 3.2GHz, 512 nVidia card.
I gave it a fair chance...
And I still hate it.:(
And it runs no more on my machine. :D

ErnestG

---

### Post by stderr on 2009-01-02
> **egalvan said:**
> Newegg had pairs of 2gig DDR2 sticks at $32, shipped...

so I over-indulged and had one too many...


As semi-pointless as it may be at the moment, there's something satisfying about sitting down at a box with 4GB+ of RAM. No matter how many memory leaks Firefox encounters... no matter how much crap I have open simultaneously... there's always space for more. UNTIL you boot a couple of VMs with generously allocated RAM ;)

TBH, that's what may push me to double up to 8GB and move to 64bit... being able to run many VMs simultaneously with no discernible performance hit.

> The problem with older machines (such as a 386) is finding software that will work, and finding repair parts.

True. I've got so many old boxes lying around here, and TBH the parts seem to circulate around all of them somehow. The funny thing being I have no use for any of them. 

> And I've now run Vista (Business Premium) for a whole day, with 8gig RAM, Core 2 duo @ 3.2GHz, 512 nVidia card.
I gave it a fair chance...
And I still hate it.:(

I vowed never to install the Vista RTM after trying goodness knows how many pre-alphas, alphas and betas. I decided to switch entirely to Linux... probably one of the best decisions I've made to date. 

"Business Premium", sounds flashy ;)

@tinivole: I must say I wasn't aware of additional functionality in 64-bit packages. Do you reckon this is somehow a direct result of a 64-bit environment, or are these additional hardware compatibilities tacked on for good measure?

---

