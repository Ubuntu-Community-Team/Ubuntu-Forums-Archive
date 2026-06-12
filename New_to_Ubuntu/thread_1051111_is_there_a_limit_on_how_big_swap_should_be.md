---
title: "is there a limit on how big swap should be?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by libihero on 2009-01-26
i'm about to extend my swap partition so that my computer can hibernate.  i want to make it a little bigger than necessary, and i was wondering if this would hinder my computer's performance.  for example, i have 2 gig ram, and i was told i need to make swap double, but i want to make it triple just in case.
and if anyone can give me a good guide to how to shrink ubuntu partition and expand swap partition, that would be great.  last time i tried to edit partitions i accidently erased my hard drive haha

---

### Post by x33a on 2009-01-26
i don't think a bigger swap will do any good or bad.

since you have 2 gigs of ram, most of the time your swap isn't even used. as for hibernation, 3-4 gigs at max should be enough.

---

### Post by philinux on 2009-01-26
Always best to seek out the ubuntu wiki.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Bit old but nothing has changed really.

---

### Post by teh_yodeler on 2009-01-26
I found it interesting that in the FAQ, it says there is no performance difference having a swap partition compared to just a regular swap file.  So having swap on a separate partition doesn't really improve performance, it just is a habit that most people are into doing

---

### Post by bodhi.zazen on 2009-01-26
A swap partition will give you a very slight boot in performance, but it would be almost impossible to measure.

The reason is swap will always be slower then RAM and is used when you are limited by insufficient RAM.

A swap file will be slower then a partition because of the over head of a file system. I seriously doubt you would notice the difference though ...

To answer the OP question ...

In general RAM is preferable to SWAP. With modern computers most people do not user more then 1-2 Gb RAM so with increasing RAM sizes swap partitions are not needed.

In fact the average user with 2+ Gb RAM can do without a swap partition.

The only thing you need swap for is hibernation, and in that case your swap partition should be slightly larger then your RAM, but NOT a Gb larger.

In general I use

swap = ram X 2 , max 1 Gb

Exception, if you use hibernation, swap = ram (or swap slightly larger then RAM)

---

### Post by teh_yodeler on 2009-01-26
Bodhi, when you say "slightly" larger for hibernation, how do you mean?

I have 2GB RAM, will a 2.5 GB swap be enough for hibernation?

---

### Post by bodhi.zazen on 2009-01-26
> **teh_yodeler said:**
> Bodhi, when you say "slightly" larger for hibernation, how do you mean?

I have 2GB RAM, will a 2.5 GB swap be enough for hibernation?

with 2 Gb ram 2.1 Gb swap should work. 

there is nothing wrong with 2.5 Gb mind you if you have the space.

I just hate it when people use the old rules and 

[indent]swap = ram X2 = 4 Gb[/indent]

4 Gb swap is , IMO excessive ;)

---

