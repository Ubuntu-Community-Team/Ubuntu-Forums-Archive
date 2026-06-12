---
title: "How do I tell if my computer is running i386 or amd64?"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by runningthemaze on 2011-07-26
I do not know what i386 and amd64 mean, although I think it has to do with the processor. I put some of my PC's specs below.
Dell Inspiron 530s
3GB RAM
Intel Pentium Dual CPU E2200 @ 2.20GHz
32-bit Windows Vista Home Premium (Service Pack 2)
64-bit capable

---

### Post by Roter1337 on 2011-07-26
Your running windows and are on ubuntuforums? Well anyway your running i386. It Means you run a 32 bit microprocessor

---

### Post by mvmacd on 2011-07-26
> **Roter1337 said:**
> Your running windows and are on ubuntuforums? Well anyway your running i386. It Means you run a 32 bit microprocessor

Haha, good point.

---

### Post by runningthemaze on 2011-07-26
Thanks.  I am here because I ran into this looking at Ubuntu (I will be downloading it shortly).

---

### Post by 007casper on 2011-07-26
i386 - 32 bit

 amd64 - 64 bit

think of 32bit as narrow freeway, and the other as wide.

---

### Post by mvmacd on 2011-07-26
> **runningthemaze said:**
> Thanks.  I am here because I ran into this looking at Ubuntu (I will be downloading it shortly).

Ah ok.  Just a quick note:  In Ubuntu, you can run the command ```
uname -m
``` in a Terminal and if it returns x86, your machine is i386 [32-bit]. if it returns x86_64 it is amd64 [64-bit].  You can also just google the CPU model number, and look at the manufacturer's specs, and see if it has "64-bit" instruction set.

---

### Post by 007casper on 2011-07-26
and then there is an extensive description over here
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by Brushstroke on 2011-07-26
You indicated in your opening post that your computer is "64-bit capable"

So I would assume it has a 64-bit processor (this means amd64) but you're just running a 32-bit Windows OS. Odd. o_O

---

### Post by CatKiller on 2011-07-26
> **runningthemaze said:**
> Intel Pentium Dual CPU E2200 @ 2.20GHz

[64-bit]("http://ark.intel.com/products/33925/Intel-Pentium-Processor-E2200-%281M-Cache-2_20-GHz-800-MHz-FSB%29").

---

### Post by 3rdalbum on 2011-07-26
You said "64-bit capable", and I'm pretty sure that CPU can run 64-bit instructions, so you could use 64-bit Ubuntu no problems.

64-bit Ubuntu is known as the "AMD64" version - it works with 64-bit Intel CPUs as well as 64-bit AMD CPUs.

---

### Post by Roter1337 on 2011-07-27
Yes. 32 Bit operating systems can run on 64 bit, but if your processor is 64 bit than you would be able to install ubuntu 64 bit.

---

### Post by runningthemaze on 2011-07-27
[URL="http://ubuntuforums.org/member.php?u=1085692"]
[/URL]

---

