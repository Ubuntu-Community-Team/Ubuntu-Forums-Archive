---
title: "What Size SWAP Partition for 3GB RAM?"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by mapes12 on 2011-04-11
Hi

In the past I've sized the Swap partition at 2x RAM. I've got my hands on a laptop with 3GB RAM but surely I don't need a 6GB swap partition..............or do I?

It's a dual core machine and so I'll be installing 10.10 64 Bit version of Ubu.

---

### Post by QLee on 2011-04-11
[QUOTE=mapes12]Hi

In the past I've sized the Swap partition at 2x RAM. I've got my hands on a laptop with 3GB RAM but surely I don't need a 6GB swap partition..............or do I?

It's a dual core machine and so I'll be installing 10.10 64 Bit version of Ubu.[/QUOTE]
Depending on what you normally do with your computer you could probably be OK with no swap. If you want to hibernate the machine then you need a swap partition of sufficient size to hold the contents of RAM. Since some compression is used in building the resume file and all your RAM isn't in use at any one time, Swap=RAM is a good figure to use for hibernation, an easy one to remember and it will be sufficient.

---

### Post by Paqman on 2011-04-11
If you need to use hibernation you need 3GB, otherwise you probably won't use swap very often (if at all). 512MB would be plenty, I tend to go for 1GB because it's a nice round number.

---

### Post by crispy_420 on 2011-04-11
I too have always read 1.5-2X RAM is the accepted norm for swap space. With hard drive space so cheap, why not it couldn't hurt. Who knows you may need it later.

---

### Post by The_Eggert on 2011-04-11
> **mapes12 said:**
> Hi

In the past I've sized the Swap partition at 2x RAM. I've got my hands on a laptop with 3GB RAM but surely I don't need a 6GB swap partition..............or do I?

It's a dual core machine and so I'll be installing 10.10 64 Bit version of Ubu.

According to the site below, you doesn't really need swap space anymore - Only when using hibernation as mentioned before :)
```
https://help.ubuntu.com/community/SwapFaq
```

---

### Post by Locke_99GS on 2011-04-11
Remember that swap space is used for two reasons:
1. When you've consumed all of your available RAM, idle or the least used processes get swapped out of RAM to the disk, opening up more RAM for whatever you're doing that requires it. The amount of swap you provide for this reason would be up to you, dependent on what kind and how many application you have, and how much RAM you have.

2. When you hibernate your machine, the contents of RAM need to be written to disk. Since RAM is volatile. and your disc (swap partition) is not, it's contents are not lost when the power is removed. This of course requires at least as much swap space as you have RAM.


I don't hibernate any of my machines, so for *me*, that particular concern is moot. I'd otherwise consider myself an average user, as far as my RAM needs go. I gave my old 2gig machine 2gig of swap, but I seldom ever touched it. My current 8gig machine also has 2gig of swap, and I of course have never touched it. Swap space is not required at all, and I will probably reclaim my swap space for something else the next time to reformat. 

So, if you ever intend on hibernating your machine, I'd make sure you have 3 or 3.5gig of swap. If you use resource hungry applications like Blender or large VM's, you may also want 2-3gig of swap. If you are just an average casual user that does email, web, music and video and the sort, you could probably get by fine without any swap space.

---

### Post by Paqman on 2011-04-12
> **Locke_99GS said:**
> When you've consumed all of your available RAM, idle or the least used processes get swapped out of RAM to the disk

Sort of. The kernel is actually a bit more clever than that, it'll generally start using swap before it runs out of RAM. You can control how keen the kernel is to use swap by adjusting the [swappiness]("https://help.ubuntu.com/community/SwapFaq#What is swappiness and how do I change it?") level.

If you've got plenty of RAM, swappiness=0 works perfectly well in my experience. The default setting of 60 is very conservative.

---

### Post by deathadder on 2011-04-12
> **mapes12 said:**
> Hi

In the past I've sized the Swap partition at 2x RAM.
The rule whereby you put aside x2 your ram for swap is a some what old rule. When limited ram was common swapping happened more and more often, now if you have over 1.5 - 2gig of RAM I'd be surprised if you hit the swap at all for most common usage. 

I've got 4gig of RAM and haven't had a swap partition in my desktop for ~4 years now...most of the time I'm either listening to music or coding and running folding@home...

---

### Post by Locke_99GS on 2011-04-12
> **Paqman said:**
> Sort of. The kernel is actually a bit more clever than that, it'll generally start using swap before it runs out of RAM. You can control how keen the kernel is to use swap by adjusting the [swappiness]("https://help.ubuntu.com/community/SwapFaq#What is swappiness and how do I change it?") level.

If you've got plenty of RAM, swappiness=0 works perfectly well in my experience. The default setting of 60 is very conservative.

:) Yes, and the x86(64) memory management system for the 2.6.38.2 kernel is 14433 lines of code, not including any calls to it from other routines. My answer was purposefully generic, as the specifics of it can easily become more than most people would want or need to know. 

Pointing out the swappiness tunable is a good thing, though.

---

