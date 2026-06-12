---
title: "New computer, partial reformat, change swap size?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Barky on 2008-12-19
I'm planning on building a new computer right after Christmas. I definitely want to keep Ubuntu on the same hard drive and plan on reformating the system partition of Ubuntu. /Home should be fine unchanged, but the swap file is questionable. The rule of thumb is 2xram, and I currently have 1GB of ram so my swap is at 2GB. If I upgrade to 3GB or 4GB of ram, do I need to expand the swap partition? Does it really matter? Thanks

---

### Post by scorchgeek on 2008-12-19
If you have 3-4 GB of RAM, your computer will probably hardly ever use the swap partition, so it should be fine. If you had, say, only 512MB of RAM, it would be much more important to have a 1GB swap partition.

---

### Post by Titan8990 on 2008-12-19
> If I upgrade to 3GB or 4GB of ram, do I need to expand the swap partition? Does it really matter? Thanks


It doesn't really matter. The more RAM you have really, the less SWAP you need. The reason for the swap should be 2x your amount of RAM is because when you put your computer in sleep mode it copies all the RAM to SWAP.


If you are like me and never sleep/hibernate then its not going to matter at all.

---

### Post by Paqman on 2008-12-19
> **Titan8990 said:**
> The reason for the swap should be 2x your amount of RAM is because when you put your computer in sleep mode it copies all the RAM to SWAP.


That's only for hibernation, suspend just powers down everything except what it needs to keep your RAM powered up.

Even for hibernation, swap still only needs to equal RAM. The swap=2xRAM rule is for older systems with not enough RAM.

For a system with 3-4GB RAM, go for swap=RAM for hibernation, otherwise swap=1GB.

---

### Post by Titan8990 on 2008-12-19
Thanks Paq, I did forget which of them copied the RAM but still tried to get my point across.

---

### Post by binbash on 2008-12-19
you will hardly use the swap with 3-4gb ram.I suggest not changing current swap size.However you should change the size if you are going to use hibernation function.

---

### Post by priegog on 2009-01-27
It seems like people are insecure about getting rid of swap altogether. For some reasons totally unrelated, I experimented with alternate filesystems (other than ext3) and in the heat of the moment of the partitions setup decided NOT to leave a swap partition. I have the gnome system monitor panel and therefore knew beforehand My computer NEVER fills up the ram (and only very rarely does so with cached data), so I took the plunge. And I've had no problems whatsoever. Mind you I only have 1.2GB RAM on this computer... 
I think with the amounts of RAM available today the whole swap concept has become outdated. Is it going to become one of those computer concepts that stick with us for the longest time because of historic inertia? Well I guess it's still useful for hibernation... But I sure as hell know that from now on, all my computers with >2gb ram won't be getting swap partitions...

---

