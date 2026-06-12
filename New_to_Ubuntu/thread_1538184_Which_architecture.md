---
title: "Which architecture?"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by peace.gangsta on 2010-07-24
It sounds quite noob and insane. I have a dell inspiron 1525 (architecture I was under impression that I was using a 32 bit one, never checked it).
I have been using 32 bit os for over 2 years. Only some days back I tried to install 64 bit ubuntu 10.04 and I succeeded. 
So I did a check and found out that it was in fact a 64 bit architecture.
So question is:Is it possible to run 32 bit operating system and all apps without even a hitch?

---

### Post by howefield on 2010-07-24
> **peace.gangsta said:**
> So question is:Is it possible to run 32 bit operating system and all apps without even a hitch?

YOu can run 32 bit or 64 bit operating systems on a bit 64 bit capable machine, but only a 32 bit on a 32 bit capable machine.

32 bit applications can be run on 64 bit operating systems, but not the other way round.

---

### Post by QIII on 2010-07-24
... but don't listen to the FUD about the problems with 64-bit OS architecture.  Very old news.  You shouldn't get alarmed by something that was going on years ago.

I remember people who doggedly held on to 16 bit architecture.  I even remember people who hung on to 8 bit architecture!  Two trains a lot of people missed.

---

### Post by cascade9 on 2010-07-24
> **peace.gangsta said:**
> It sounds quite noob and insane. I have a dell inspiron 1525 (architecture I was under impression that I was using a 32 bit one, never checked it).
I have been using 32 bit os for over 2 years. Only some days back I tried to install 64 bit ubuntu 10.04 and I succeeded. 
So I did a check and found out that it was in fact a 64 bit architecture.
So question is:Is it possible to run 32 bit operating system and all apps without even a hitch?

For x86, you can run 32bit on a 64bit capable CPU with no issues (there are other architechtures where there is no 32bit version). Since AMD64 (or x86-64 if you perfer) is just extensions to x86, its fine. 

BTW, I agree with QIII, 64bit is mature these days, and if you have a 64bit CPU then you might as well use it.

---

### Post by Simian Man on 2010-07-24
The only real reason not to use 64-bit is if you have less than a gig or so of RAM as 64-bit takes up a bit more memory.

---

### Post by Goolie on 2010-07-24
64 bit OS, 32-bit / 64-bit Apps.

32-bit OS, 32-bit apps.  =D

When I first got Vista 64-bit a LONG time ago, I had alot of problems running 32-bit apps, but that was a long time ago, and I don't think the arch's have that sorta problem anymore.

---

### Post by peace.gangsta on 2010-07-25
> **Goolie said:**
> 64 bit OS, 32-bit / 64-bit Apps.

32-bit OS, 32-bit apps.  =D

When I first got Vista 64-bit a LONG time ago, I had alot of problems running 32-bit apps, but that was a long time ago, and I don't think the arch's have that sorta problem anymore.
Yeah I agree.I have heard people complaining about lack of software support etc for 64bit.But till now I haven't encountered any trouble. All good and going.\\:D/
But to find out configuration of your system after 2 years of use, is a revelation in fact.

---

### Post by crutch on 2010-07-25
I don't think it makes a great deal of difference. Personally I recently switched back to 32 bit because occasionally had a few problems with some (proprietary) applications, such as Lotus Office (I think this only has a 32 bit version) You can almost always install them on a 64 bit system, but sometimes you have to jump through a few extra hoops

---

### Post by lisati on 2010-07-25
IMO 64-bit support **is** getting better. I've been running 10.04 64-bit on my laptop for a while now, and haven't run into any major problems.

---

### Post by WRDN on 2010-07-25
64 bit support is improving, but there are still some programs to be wary of. 32bit flash under Linux is still superior to the 64bit counterpart.
Other than flash, most apps I've used have been fine and run without any problems.

---

### Post by pmn9393 on 2010-07-25
I know this sounds odd, but is there a "128 bit" for quad core processors, and if so, will there be another version for it? I know that there are no 128 bit command sets being used in quad core processors, but i mean something optimized for quad core.

---

### Post by WRDN on 2010-07-25
> **pmn9393 said:**
> I know this sounds odd, but is there a "128 bit" for quad core processors, and if so, will there be another version for it? I know that there are no 128 bit command sets being used in quad core processors, but i mean something optimized for quad core.

Modern multi-core CPUs have a 64bit instruction set. It is the kernels job (more specifically, the scheduler), to optimise work across the cores so as to use them to their fullest potential. Assuming the application has been programmed to use multiple threads, [SMP (Symmetric multiprocessing)]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing") can be employed.
What also must be considered is CPU specific features. For example, Intel CPUs have Hyperthreading technology, to allow 2 threads to run on 1 core at the "same time". 
AMD CPUs may have something similar, I cannot comment on it though.

---

