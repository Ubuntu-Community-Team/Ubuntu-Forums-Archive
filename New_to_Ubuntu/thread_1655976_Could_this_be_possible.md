---
title: "Could this be possible"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by a.taylor352 on 2010-12-30
I am running a eee pc 1005peb with the n450 Atom, 1 gb ram, 250gb HD with 10.04LTS(because windohs 7 blows)
What I am wondering is because I have the express gate button does that force the bios to load a certain partition in the drive? I have fully formatted the drive when I did a fresh 10.04 install. Also I am big on music and was wondering if I could make a simple linux OS that would load from the "express gate" partition but would be severely limited to only music access with hard drive spin down, loading 100+songs into ram and other limitations to fully optimize battery life. As it sits I have a literal battery life of 6 hrs and would like to get like 11 of pure music with a fast boot time.

---

### Post by cascade9 on 2010-12-30
Express gate = asus rebranding of 'splashtop'. Its not a on a HDD partition, its a surface mounted flash drive- 

[http://en.wikipedia.org/wiki/Splashtop](http://en.wikipedia.org/wiki/Splashtop)

It is possible to mod expressgate, eg- 

[http://www.sierrasoftworks.com/expressgate](http://www.sierrasoftworks.com/expressgate)

WARNING! I have not tested any of these mods. 

But its not going to help you....if your HDD spins down, how will you get your music?

---

### Post by a.taylor352 on 2010-12-30
can you copy them into a temporary fake partition created in ram? I would assume kind of like the opposite of a swap space.
I had a sony cd player that used to load quite a few tracks of a song into ram(i guess) and then spin down the cd. I could drop the cd player from 4 ft and it would never skip

---

### Post by Paqman on 2010-12-30
> **a.taylor352 said:**
> can you copy them into a temporary fake partition created in ram?

I don't know much about Splashtop, but most Linux distros have /dev/shm available to use as a ramdisk. If you copy your stuff to there, it's in RAM, not your hard drive.

But you've only got 1GB of RAM to play with, so it's debateable whether a ramdisk would reduce disk usage much, since the more you fill up your RAM, the more likely the system is to start swapping to disk (assuming Splashtop swaps to disk that is...)

---

### Post by a.taylor352 on 2010-12-30
Well I have considered upgrading to 2 gbs of ram anyways. As it sits my ubuntu 10.04 uses about 245mb of ram at idle. I figure with a stripped down os with only the required programs and a simple to use mp3 player I would have ample amounts of extra ram to pre-load at least 1gb of music(if expanded to 2gb)(which is more than half of all that I have.) im just not sure if it's possible. Unfortunately I am not that inclined to figure it out myself :(

---

### Post by cascade9 on 2010-12-31
You simply arent going to double your battery life just by makign a RAM disc. 

The HDD probably drags 1-1.5watts at idle, 1.5-3watts reading or writing. Considering that your eee pc 1005peb is around 20watts idle, 26-28watts at load, disabling the HDD would save you 10% or less of your power consumption. 

You might go from 6hrs to 7hrs, but thats at best.

---

### Post by Kellemora on 2010-12-31
I'm not being a smart **** here.  But wouldn't it be simpler to use extra battery packs or a larger capacity battery pack?

If the mfgrs. battery packs are too expensive, pick yourself up a Deep Cycle Marine Battery (gel cell, motorcycle battery size, 12 to 15 bucks) and use your DC adapter cord.

I had a couple of laptops where they wanted over 50 bucks for their scrawny short lived battery pack.  Since I had the carry case already and the Gel Cell Battery fit into it nicely, I was never without power.

But I still prefer a REAL computer, which can be made portable easily enough if need be.  AKA Bag computer!

TTUL
Gary

---

