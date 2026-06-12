---
title: "WHere is all my ram???"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by bustedbit on 2010-05-08
Ok, I know for a fact that I have 4 gigs of physical ram, but Ubuntu tells me I only have 2.8.  Why is this???  Any help would be appreciated.

---

### Post by howefield on 2010-05-08
Are you running 32 or 64 bit Ubuntu ?

32 bit will see much less than 4 gig, and if you have integrated graphics taking shared memory, you will be left with even less.

---

### Post by bustedbit on 2010-05-08
Yea, it's 32 bit (unfortunately).  As long as I'm still using all of it, I'm ok, I guess, I just want to make sure that 1.2 isn't just going to waste.

---

### Post by steveneddy on 2010-05-09
So the OS can "see" all four gigs of ram you need to use the 64 bit version of Ubuntu

---

### Post by Speed_arg on 2010-05-09
Doesn't ubuntu has PAE?

---

### Post by shae on 2010-05-09
The desktop version does not have PAE.  You can install the kernel from the server and get that working.

---

### Post by 3rdalbum on 2010-05-09
> **bustedbit said:**
> Yea, it's 32 bit (unfortunately).  As long as I'm still using all of it, I'm ok, I guess, I just want to make sure that 1.2 isn't just going to waste.

Well yeah, it is going to waste. A 32-bit system can only see 4 GiB of RAM in total, INCLUDING any memory that is sitting inside peripherals in your computer or chipsets on your motherboard.

So, if you have a 512MiB graphics card, that 512 MiB is taken out of the 4 GiB of addressable memory. That portion of your RAM is sitting idle, unaddressable.

If you use a PAE kernel or a 64-bit system, then you have much more address space, and the parts of your computer that have their own memory can be addressed without overlapping your RAM.

---

