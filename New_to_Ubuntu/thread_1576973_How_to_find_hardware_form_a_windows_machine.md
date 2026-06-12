---
title: "How to find hardware form a windows machine?"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by geirknappen on 2010-09-18
If someone has windows, and they want me to help them get linux, then I should probably try to find out what computer architecture and processor they have, so that I determine if they need the 32 -bit or the 64 bit version, or because of hardware can't use ubuntu.

What windows programs exist for figuring out such things? Maybe I should just give them the 32 bit, and say that it is a high probability its gonna work?

If they have i686 architecture and amd turion 64 x2 processor, what to give them? Is it the architecture or the proseccor that is supposed to be 64-bit?

---

### Post by cascade9 on 2010-09-18
Theres more hardware analysis tools for windows than you can poke a stick at. More than you and serveral friends, all armed with sticks could poke at for that matter....

CPUz is good- 

[http://www.cpuid.com/softwares/cpu-z.html](http://www.cpuid.com/softwares/cpu-z.html)

AFAIK it wont actually tell you if its a 32bit or 64bit CPU, you need to do that yourself. Probably the easiest way to find out if the CPU is 64bit is with a  liveCD (lshw, check for the 'lm' or 'x86-64' flags in the CPU capabilities output). Aside from that, try checking wikipedia, AMD or Intel sites to find out. 

There are other tools that I can think of just of the top of my head- belarc advisor (gives more than you really need) and everest (nice, but I'd rather use CPUz over a 'trial' version). 

Anything which meets 10.04 requirements for 'desktop' use (1GHz CPU) will be i686 or later architecture. 

I've never seen windows return anythign like 'i686'. Not saying that its impossible, I've just never seen it. You'll just get '32bit' or '64bit' from windows.

---

### Post by geirknappen on 2010-09-18
> **cascade9 said:**
>  Probably the easiest way to find out if the CPU is 64bit is with a  liveCD (lshw, check for the 'lm' or 'x86-64' flags in the CPU capabilities output). 

What exactly to do? If I use a live ubuntu cd to try to identify what computer architecture a computer has, isnt it best to use the 32-bit live cd, and type a command into the terminal which gives me the information i need? Will a computer be damaged if i use a 32 bit cd instead of the 64 bit cd, if the computer has 64 bit architecture?

---

### Post by CharlesA on 2010-09-18
> **geirknappen said:**
> What exactly to do? If I use a live ubuntu cd to try to identify what computer architecture a computer has, isnt it best to use the 32-bit live cd, and type a command into the terminal which gives me the information i need? Will a computer be damaged if i use a 32 bit cd instead of the 64 bit cd, if the computer has 64 bit architecture?

It won't do any damage if you run a 32-bit livecd on a 64-bit machine.

I keep a 32-bit livecd with no at all times, in case I need it. :P

Anyway, you'd run this command:

```
lshw | grep x86

```

If it says x86-64, it's a 64-bit CPU. :)

---

### Post by davidmohammed on 2010-09-18
... deleted - previous guy got there first!

---

### Post by cmcanulty on 2010-09-18
In windows just rt cl computer on start menu, properties and it give all that in the general tab.

---

### Post by srs5694 on 2010-09-18
> **geirknappen said:**
> What windows programs exist for figuring out such things? Maybe I should just give them the 32 bit, and say that it is a high probability its gonna work?

As already mentioned, [CPU-Z](http://www.cpuid.com/softwares/cpu-z.html) (aka CPUID) is a good Windows tool for checking hardware specifications. It's been a while since I've used it, but judging by the screen shot on the home page, it does report whether the CPU is 64-bit capable -- note the "EM64T" in the "Instructions" field in the screen shot. (Intel calls its x86-64 CPUs "EM64T." AMD uses the term "AMD64.")

If you know the make and model of the CPU, you can also look up its specifications on the manufacturer's Web site or various other places. There's probably a Wikipedia entry (or two or three or four) that contain the information, for instance.

Certainly using a 32-bit x86 distribution is a safe approach, in the sense that it will work on most hardware. (Old PowerPC-based Macs and some other exotic systems are exceptions to this rule.) OTOH, a 64-bit x86-64 distribution will be slightly faster and better supports large amounts of memory.

> If they have i686 architecture and amd turion 64 x2 processor, what to give them? Is it the architecture or the proseccor that is supposed to be 64-bit?

In this context (used to distinguish 32- and 64-bit systems), "processor" and "architecture" are synonymous.

> Will a computer be damaged if i use a 32 bit cd instead of the 64 bit cd, if the computer has 64 bit architecture?

No. One of the key features of the x86-64 architecture is that it can run 32-bit software, including OSes, without problems. In fact, prior to Windows 7, most 64-bit systems shipped with 32-bit versions of Windows, at least judging by what I saw in stores. You just won't be taking full advantage of the hardware if you use a 32-bit OS on x86-64 hardware.

FWIW, six years ago I wrote [this article for Linux Magazine](http://www.linux-mag.com/id/1699) about the x86-64 platform. (Free registration is required to read the whole article.) Although many of the specifics have changed, the fundamentals remain the same as they were back then. If you want to understand the basics of what 32- vs. 64-bit buys you, it may be a useful read.

---

### Post by cascade9 on 2010-09-19
> **srs5694 said:**
> As already mentioned, [CPU-Z]("http://www.cpuid.com/softwares/cpu-z.html") (aka CPUID) is a good Windows tool for checking hardware specifications. It's been a while since I've used it, but judging by the screen shot on the home page, it does report whether the CPU is 64-bit capable -- note the "EM64T" in the "Instructions" field in the screen shot. (Intel calls its x86-64 CPUs "EM64T." AMD uses the term "AMD64.")

Well, I was wrong. :) Thanks for that info, stored for later use. 

I didnt even look at the screenshot that hard to be honest, I havent used CPUz for years. That was a few years ago, and I was mianly working on 2nd hand machines and repairing borked and semi-borked systems. For some reason, my bosses thoguht that ripping the side of and eyeballing was 'less professional' than using some software to tell the hardware in the system, so they made me use CPUz before I'd get the screwdriver out. Even though in 99% of cases, the side was going to come off, and it was faster for me to pick the hardware by eyeball than booting windows on a Pentium I/2/3.....

---

### Post by geirknappen on 2010-09-20
> **srs5694 said:**
> As already mentioned, [CPU-Z](http://www.cpuid.com/softwares/cpu-z.html)

In this context (used to distinguish 32- and 64-bit systems), "processor" and "architecture" are synonymous.


Alot of usefull info. He had a sticker with amd turion 64 x2 on his laptop, so I guess I give him a 64 bit cd. He wants to wait for ubuntu 10.10 (That is 3 weeks from now.)

---

### Post by geirknappen on 2010-10-03
Some people say that as long as I have less than 2 gb ram, it makes no sense to install the 64 bit version, even if it is a 64 bit architecture. Some people say the 32- bit is more solid. Is there some truth to this?

---

