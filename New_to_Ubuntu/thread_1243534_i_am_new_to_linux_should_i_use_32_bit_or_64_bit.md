---
title: "i am new to linux should i use 32 bit or 64 bit"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by sublimemovement on 2009-08-18
I am new to Linux and I was wondering if I should use the 32 bit or 64 bit version.

I have an AMD athlon 64 x2 dual core processer+  
          slot: Socket M2
          size: 2100MHz
          capacity: 3GHz
          width: 64 bits
          clock: 1GHz
And I have 4 GiB of memory.

My mainly use my computer for going on the Internet, music, movies, and games.

I will be doing a dual boot with vista and I mostly want to learn how to use Linux.

thanks

---

### Post by theozzlives on 2009-08-18
With 4 GB RAM, I would say 64 bit.

---

### Post by wizard10000 on 2009-08-18
> **sublimemovement said:**
> I am new to Linux and I was wondering if I should use the 32 bit or 64 bit version.

I have an AMD athlon 64 x2 dual core processer+  
          slot: Socket M2
          size: 2100MHz
          capacity: 3GHz
          width: 64 bits
          clock: 1GHz
And I have 4 GiB of memory.

My mainly use my computer for going on the Internet, music, movies, and games.

I will be doing a dual boot with vista and I mostly want to learn how to use Linux.

thanks

I'd install the 64-bit version.  Hardware support is pretty good - especially for hardware that's a little older.  I'm running Jaunty 64-bit on a Core i7 and everything works right except hardware monitoring and that should be coming soon.

---

### Post by sublimemovement on 2009-08-18
Thanks for the quick reply. I just was not sure I would have hardware support issues using the 64 bit version.

thanks again

---

### Post by nhasian on 2009-08-18
64 bit is great.  we even have a 64 bit java and flash.  life is good :)

---

### Post by kuja on 2009-08-18
> **wizard10000 said:**
> I'd install the 64-bit version.  Hardware support is pretty good - especially for hardware that's a little older.  I'm running Jaunty 64-bit on a Core i7 and everything works right except hardware monitoring and that should be coming soon.

It's supported as of kernel 2.6.29, so you can compile a newish kernel or wait for Karmic.

---

### Post by Ric_NYC on 2009-08-18
I have a 64 bit computer. I tried the 64 bit Ubuntu version.
Then I decided that a 32 bit would give me more applications running. 
I'm happy running a 32 bit version of Ubuntu in a 64 bit computer.

:)

---

### Post by wizard10000 on 2009-08-18
> **kuja said:**
> It's supported as of kernel 2.6.29, so you can compile a newish kernel or wait for Karmic.

Guess I'll wait the two months  ;)

---

### Post by k3lt01 on 2009-08-19
My fathers laptop is an amd64 bit, it originally come with 32 bit Vista so I initially installed 32 bit Ubuntu 8.04 iirc. I then downloaded and installed 64 bit Ubuntu 8.04 and we have stayed with 64 bit ever since.

Soooooo, if you have the RAM, which you do, and a processor capable of using it then I would advise going 64 bit.

---

### Post by Nburnes on 2009-08-19
64 bit is great IMO

---

### Post by riazrahaman on 2009-08-20
Go for 64bit. Have been using 64bit on my desktops and laptops for more than a year now.

Performance is very good.

---

### Post by Grenage on 2009-08-20
It becomes a lot more important when you have more than 3.5-4GB RAM, but I recommend it on any 64-capable system.

---

### Post by Cheesemill on 2009-08-20
There's no reason not to use 64-bit.

---

### Post by Grenage on 2009-08-20
> There's no reason not to use 64-bit

There are plenty of things that _won't_ run on AMD64 architecture, and I have in some instances been forced to use x32; thankfully they are uncommon enough that your average user won't run into problems.

---

### Post by Copernicus1234 on 2009-08-20
I have yet to see any real performance benefits from 64-bit. Sure it will make games run a few fps faster, but will it affect application performance, bootup times etc? I dont see it.

The advantage of being able to use extra memory is nice, but I really dont see any other incentive. Maybe someone else does?

---

### Post by Grenage on 2009-08-20
Yes and no.  AMD64 is theoretically faster, although it's generally marginal.  The main benefit is better use (or use at all) or larger memory sets.

---

### Post by Hamchan on 2009-08-20
> **Grenage said:**
> Yes and no.  AMD64 is theoretically faster, although it's generally marginal.  The main benefit is better use (or use at all) or larger memory sets.

Is that really a noticeable benefit for the average user? I'm running the 32 bit Ubuntu on a machine with 4 gigs of ram. Sure, it only allows me to use 2.95 gigs, but I'm only using 323 megs right now and have only once broken the 2 gig barrier when I was playing with a virtual machine.

How many people actually have a use for 4 gigs of ram and consider themselves "Average Users?"

---

### Post by Grenage on 2009-08-20
> How many people actually have a use for 4 gigs of ram and consider themselves "Average Users?"

Rather a lot, these days.  Few computers worth buying come with less than 4GB of RAM.  The differences are noticeable to some extent for the average user, so it's uncommon that someone could justify running x32 over x64.

---

### Post by wizard10000 on 2009-08-20
> **Hamchan said:**
> How many people actually have a use for 4 gigs of ram and consider themselves "Average Users?"

As you mentioned anybody doing virtualization.  I generally allocate 4GB of RAM to a VM.

---

### Post by 3rdalbum on 2009-08-20
Windows has difficulty with 64-bit because many software developers wrote their programs and drivers with the assumption that they would only be used on 32-bit x86 processors, because that's mostly all Windows would run on.

When 64-bit came around, they were disadvantaged because their code was not written to be portable to 64-bit architecture, and even if it was, users relied on the developer releasing a recompiled 64-bit version (because Windows-based developers don't release their source code).

Linux developers have always written their programs to be portable to other processor architecture, because Linux runs on so many of them. If your program runs on x86 32-bit, Arm, PowerPC, MIPS and SPARC, it is pretty much guaranteed that it can be just recompiled to run on 64-bit x86.

And users don't have to wait for the developer to recompile the software - they can do it themselves, because most Linux software is open-source.

As a result, Linux works very well on 64-bit and in regular use it's indistinguishable from 32-bit.

---

