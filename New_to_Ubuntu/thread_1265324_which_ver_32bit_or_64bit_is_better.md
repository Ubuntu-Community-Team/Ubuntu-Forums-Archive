---
title: "which ver 32bit or 64bit is better?"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by aljoriz on 2009-09-13
I know the answer is dependent upon your CPU.  Firstly, I am using a AMD64 Athlon processor with 2g ddr2 800mhz ram.

I used windows7 a month ago prior to my current OS.  I tried the 64-bit version and found that my computer crawled, installed the 32-bit version of the win7 and I can see a huge difference in performance.  

In ubuntu, IS the 64-bit version limited to new CPUs that uses quad or dual tech?or can the dated amd 64 like athlon be fast suited for the 64bit version?

---

### Post by philinux on 2009-09-13
[http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

---

### Post by NoaHall on 2009-09-13
64 bit is better. Always better. Even without more than 3.4GB, it can process the native apps twice as fast. So, you get a computer running twice as fast while running most things. Some people will claim that it's unsupported, but to be honest, there's no problems at all installing anything. Flash for 64 bit is in a solid alpha, and it runs better than the one native to 32 bit on 32 bit OS's! 

64 bit is the future.
64 bit is the way...

---

### Post by 3rdalbum on 2009-09-13
> **NoaHall said:**
> Even without more than 3.4GB, it can process the native apps twice as fast.

No. 32-bit and 64-bit don't refer to the amount of data that can be processed in a certain amount of time. They refer to the "size" of numbers that can be natively worked with in the CPU. 64-bit CPUs can use "longer" memory addresses, which give them the ability to access more memory. 64-bit CPUs can process "long" numbers in one clock cycle, rather than the two or more clock cycles that it takes a 32-bit CPU.

Unless all your computer does is video transcoding or scientific calculations, then you won't get anywhere near a 2x speedup.

To answer the OP's question, it's not so much a case of "Should I use 64-bit" as "Why shouldn't I use 64-bit?". 64-bit is well and truly "here" on Linux and if you have a supported CPU and ample RAM, then I honestly can't think of a reason not to use 64-bit Linux.

I use it on all the 64-bit-capable machines in my care. Two of those are owned and used by people who are new to Ubuntu.

---

### Post by NoaHall on 2009-09-13
I know that. But 64 bit apps are made to run using the 64 bit coding,and the processor can address these twice as fast. So yes it is twice as fast.

However, a lot of apps still have bits of 32 bit coding in them, so there's less of a gain.

---

### Post by SuperSonic4 on 2009-09-13
Use the 64bit, there is only negligible differences for the average user but when you do need CPU intensive tasks it will help

---

### Post by binbash on 2009-09-13
Use 64 bit.

---

### Post by mcduck on 2009-09-13
> **NoaHall said:**
> I know that. But 64 bit apps are made to run using the 64 bit coding,and the processor can address these twice as fast. So yes it is twice as fast.

However, a lot of apps still have bits of 32 bit coding in them, so there's less of a gain.

Still not true. :)

64-bit processors are only quicker in those tasks that actually need to calculate things with the higher precision 64-bit numbers. Most of the things you do don't use that large numbers or precision for anything, and thus get no benefits.

It doesn't matter if the program is compiled to use 64 bits or not, it's simply a question of if the actual task being done benefits from larger numbers/higher precision. Hardly any task involved in daily computer usage do. Some photo editing tasks can benefit from 64 bits, as can other CPU-intensive multimedia tasks like video editing and audio production. And of course scientific simulations.

Still, if you have a 64-bit CPU there's no reason not to run a 64-bit OS as well. It might not give you better performance (depending on what you use your computer for), but it won't reduce performance either. ;)

---

### Post by NoaHall on 2009-09-13
Meh, you all just hate me. I run apps which use the full 64 bit almost all the time, so I benefit a lot.

---

### Post by philinux on 2009-09-13
> **NoaHall said:**
> Meh, you all just hate me. I run apps which use the full 64 bit almost all the time, so I benefit a lot.

Which apps?

---

### Post by NoaHall on 2009-09-13
Well, games , flash and VirtualBox. 

Compiling things is a lot quicker too, and my system generally runs more smoothly

---

### Post by shae on 2009-09-13
Wine + 64bit = PITA

Use 32bit, especially if you want to use wine.

---

### Post by NoaHall on 2009-09-13
My wine runs fine as 64 bit. Can play and run lots of games. Get up to date.

---

### Post by aljoriz on 2009-09-13
most of the post here are really tempting me to go 64bit.  The hassle of downloading and installing most of the stuff is just what I hate.

---

### Post by aljoriz on 2009-09-13
with Karmic going out in a next month, waiting should be a better option.  Thank you so much guys!  when Karmic goes out, I will definitely go 64bit.  I was just concerned that the 64bit xubuntu MIGHT slow my system down like win7 64-bit did.

---

