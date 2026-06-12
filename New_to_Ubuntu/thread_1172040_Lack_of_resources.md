---
title: "Lack of resources"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by choochoo22 on 2009-05-28
What consequences take place when Ubuntu 9.04 runs out of memory or swap space?  I have been experiencing frequent crashes and I'm wondering if the cause is lack of resources.

---

### Post by jimmy the saint on 2009-05-28
How much ram do you have?  You would need to be doing a lot to run out of ram on a modern system with Ubuntu and 1+Gig of ram and a decent swap.

---

### Post by Kevbert on 2009-05-28
When you run out of RAM the swap space is used. If you run out of swap space you may get system freezes and/or crashes. Here's [COLOR="Red"][a guide]("https://help.ubuntu.com/community/SwapFaq")[/COLOR] on swap and how to add more.

---

### Post by choochoo22 on 2009-05-28
It's an older system with 256MB memory.  The installation guidelines said things generally work well with the swap space set equal to the memory size but since this memory is a bit small, I believe I set the swap partition to about 750MB plus an 8MB leftover space on another disk.  The failure mode I keep experiencing is a total system freeze where the only thing responding is the mouse pointer.  I'll try adding a swap file and see if that helps.

---

### Post by SunnyRabbiera on 2009-05-28
Yeh Ubuntu Jaunty would probably run very sluggish on that kind of system.
Do you know what brand is your video card is too?
Memory is one half of the issue but video can be a big fsactor too.
If you use a intel graphics card then severe slowdown is in your future sorry to say.

---

### Post by XCan on 2009-05-28
Here some kind of peak memory usage logging script would really be helpful. I suck too much to be able to write such a script and have failed to find one, but perhaps someone else have a clue?

---

### Post by choochoo22 on 2009-05-28
I wasn't expecting blazing performance but I wasn't expecting lockups either.  The video card is an ATI All-in-wonder.  I know the tuner is not supported in Linux but the display seems to work OK.

---

### Post by LowSky on 2009-05-28
256 RAM is barely enough, especially if the processor is under 1 GHz.

If you need the thing running may I suggest another Linux Distro like Puppy or DSL, both are made to run on lower end machines

---

### Post by NHArticleTen on 2009-05-28
> **LowSky said:**
> 256 RAM is barely enough, especially if the processor is under 1 GHz.

If you need the thing running may I suggest another Linux Distro like Puppy or DSL, both are made to run on lower end machines

Yes, the latest release of Puppy Linux is quite nice.  Damn Small Linux is great too.  Definitely better to experiment with since they can be re-installed in a few minutes when you break them.

---

### Post by Kevbert on 2009-05-29
> **choochoo22 said:**
> It's an older system with 256MB memory.  The installation guidelines said things generally work well with the swap space set equal to the memory size but since this memory is a bit small, I believe I set the swap partition to about 750MB plus an 8MB leftover space on another disk.  The failure mode I keep experiencing is a total system freeze where the only thing responding is the mouse pointer.  I'll try adding a swap file and see if that helps.

Even Xubuntu will run slow on a PC with that amount of memory. If you can upgrade the memory. Alternative operating systems such as Crunchband (based on Ubuntu) or Puppy will work much better.

---

### Post by choochoo22 on 2009-05-29
I followed Kevbert's link to add a swap file.  Since there is plenty of disk space, I made it 1Gb.  With the system loaded as before, the "free" command is showing only about 160Mb being used.  There was 750Mb available even before the swap file was added.  However, the system hasn't crashed since the swap file was added.  Perhaps it was seeing some much higher peaks.

It's too soon to say this problem is solved but I am hopeful.  If I get more crashes  I will try one of the smaller installations.

Thanks for the help.

---

