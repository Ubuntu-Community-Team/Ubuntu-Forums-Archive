---
title: "cpu confusion"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by ubunterooster on 2010-03-09
I don't understand how cpu speeds go so tell me how my guess is:

cpu A is a dual-core chip @ 1.5 ghz
cpu B is a quad-core @1.5 ghz
cpu C is a quad-core @ 3.0 ghz
cpu D is a quad-core [with hyper-threading] @3.0 ghz

so in a contest of transcoding 1000 audio files:
1, B is twice as fast as A
2, C is twice as fast as B
3, D is twice as fast as C
???
[yes, I know I have over 200 beans but the above is not mentioned in any of my books besides saying "higher cpu speed is better"]

---

### Post by audiomick on 2010-03-09
As far as I know, basically correct, although I have no idea how much speed gain hyperthreading brings. What makes it complicated is how the OS and the programs use the multiple cores.
A program that can't use more than one core will be just as fast/slow on A and B, and "twice" as fast on C because the core is faster, with an additional speed increase on D with the hyperthreading.
A program that spreads the load optimally on all cores will be faster according to what one would expect from the specifications.

---

### Post by ubunterooster on 2010-03-09
Thanks. I'm glad to get that figured out.

---

### Post by cascade9 on 2010-03-09
> **ubunterooster said:**
> I don't understand how cpu speeds go so tell me how my guess is:

cpu A is a dual-core chip @ 1.5 ghz
cpu B is a quad-core @1.5 ghz
cpu C is a quad-core @ 3.0 ghz
cpu D is a quad-core [with hyper-threading] @3.0 ghz

so in a contest of transcoding 1000 audio files:
1, B is twice as fast as A
2, C is twice as fast as B
3, D is twice as fast as C
???
[yes, I know I have over 200 beans but the above is not mentioned in any of my books besides saying "higher cpu speed is better"]

Not really. If everything is equal, its not that far from the truth, but they arent.....

Besides the valid point audiomick put up about programs that will or wont use multipule cores (ie if the program is single core only, you can add as many cores as you want and it wont make any difference) there are other considerations- 

Architecture, front side bus, memory speed, and CPU cache figure heavily. 

To use an example- this is why a Intel Core 2 Quad Q9550(2.83Ghz, 12MB L2 cache) is faster than a Intel Core 2 Quad QX6800 (2.93Ghz, 8MB L2 cache). Same basic architecture, but more L2 cache = better preformance. On some programs anyway. 

I can dig up more examples if you really want. ;) 

BTW, even if everythign else was equal (which it isnt but thats already covered) hyperthreading will not give you x2 performance of a not hyperthreaded CPU. Its basicly 'fake' multicoring, there isnt the extra cores avaible but it allows programs to run as though there is extra cores avaible. I cant recall how much of a perfromance gain it gives...its not even possible to give a hard 'it will give x% increase' due to different programs reacting differently to hyperthreading. 

For example (and these are totally made up numbers), it might give a 25% increase on a CPU with 8MB cache for a program that uses very little L2/L3 cache, but only give 5% on a program that uses L2/L3 heavily.

---

### Post by J V on 2010-03-09
Hyperthreading is a waste, it only gives a 30% speed bump or so...

Better to have the extra CPU power from disabling it

If ubuntu uses 10% when idle (thats a lot but lets imagine) then on a 1Ghz Qcore its doing 400 mhz...

Always...

If you add another Ghz, its not going to seem like double because thers still that 400 mhz missing... then there are things like architecture, L-cache memory (or whatever that super speed 56k is called that surrounds the cpu) etc...

---

### Post by ubunterooster on 2010-03-09
So I understand L-cache to be somewhat similar to RAM then, which explains some crashes.
 
  Thanks all, now I have to make a comprimise between speed and TPD and I can pick out a new CPU. 
[AMDs entry level Quad-core looks best so far]

---

### Post by Kellemora on 2010-03-10
I Know NOTHING, except this!

I have two IDENTICAL computers, same Mobo, same Memory, same HD, etc.

The ONLY difference between the two is one used a quad core, the other a dual core, both AMD, the dual core is a 5200, forget what the quad core was as it took a hit and we had to replace it, the mobo and the power supply.

I used them side by side for nearly 4 months, and the dual core was significantly faster than the quad core in almost everything we did.

WHY I don't know!

My thought about it is a dual core CPU might just be only 1/2 of single core and a quad core only 1/4 of a single core.  I know, NOT logical.
But that is the WAY my computers acted!

Either that or most of our programs could only see ONE CPU and the other one (or 3) sat idle while ONE did all the work?

And oddly, almost all of my OLD 32 bit computers are faster than the two newest 64 bit computers.  All running Ubuntu 8.04 LTS.....

TTUL
Gary

---

### Post by ubunterooster on 2010-03-10
My understanding is each individual core was slower but together they usually add up to more. Many uses only effect one core.

---

### Post by undecim on 2010-03-10
Higher numbers of cores are generally better for multi-tasking. High core numbers are popular on servers, because they do several things at once.

As far as hyper-threading is concerned, I don't see how it is supposed to make things faster. Supposedly, each core has two "virtual cores" and the real core handles both virtual cores equally.

But doesn't the kernel handle this kind of thing already? You can still multi-task on a single-core system because the kernel shares processor cycles with all the threads running. Seems like it would be better not to lie to the kernel about the number of cores and let the kernel decide how to distribute the work. The kernel might have two cpu-intensive threads, but what if it puts both those threads on virtual processors that are run by the same core?

Or am I completely misunderstanding something?

---

### Post by egalvan on 2010-03-10
> **Kellemora said:**
> 

I have two IDENTICAL computers, same Mobo, same Memory, same HD, etc.

The ONLY difference between the two is one used a quad core, the other a dual core, both AMD,
 the dual core is a 5200, forget what the quad core was as it took a hit and we had to replace it, the mobo and the power supply.

, and the dual core was significantly faster than the quad core in almost everything we did.

WHY I don't know!


Without knowing WHICH quad you had, there is no way to compare.

L1, L2, L3 cache sizes,
Hypertransport Links
core speed

All of these affect the final *quickness* of a CPU.

Quad-cores tended to clock slower than dual-cores, due to heat issues.

And differences in the motherboard could also account for it
(I know, you say you had the *same mobo*, but was it set up *identically*? mobo revision level? BIOS settings? BIOS revision level?)

> 
My thought about it is a dual core CPU might just be only 1/2 of single core and a quad core only 1/4 of a single core.
  I know, NOT logical.
But that is the WAY my computers acted!


Nope, not logical.
 AMD, unlike Intel, always had discrete cores, they never used *fake* cores (Intel Hypethreading).
They also used dedicated core interconnects (far faster), unlike Intel which used the FSB (far slower), and they used on-die memory controllers (far faster)

> Either that or **most of our programs could only see ONE CPU **and the other one (or 3) sat idle while ONE did all the work?

Almost always the case. Software is slowly being re-written/re-compiled to use multi-cores.

> And oddly, almost all of my OLD 32 bit computers are faster than the two newest 64 bit computers.  All running Ubuntu 8.04 LTS.....

This is trickier... 
32bit? 64bit? How much RAM? which CPU? Which motherboard (chipset)?
Far too many variables to pin down.

---

### Post by ubunterooster on 2010-03-10
@undecim: I understand now, and agree. [so...Hyperthreading gets the media hyped up, little else. meh.]

---

### Post by egalvan on 2010-03-10
> **undecim said:**
> 
As far as hyper-threading is concerned, I don't see how it is supposed to make things faster. Supposedly, each core has two "virtual cores" and the real core handles both virtual cores equally.
Or am I completely misunderstanding something?

Intel´s first dual-core CPU`s were called virtual because only part of the core was duplicated.

It was one core with a few extra parts, mainly the pipe-lines, being `dual`

It gave *some* speed advantage, but it was not great.
Software had to be optimized to use the dual-threads.
(Adobe Photoshop was one resounding success story. it also ran slowly on AMD, much to Intel`s delight)

Hyperthreading was mainly marketing to keep Intel users from jumping ship to the (at that time) vastly superior AMD Dual-Core CPU. It gave Intel much-needed time to improve their architectures.

And even the firt true-dual-core Intel chips were inferior to the AMD offerings. 
Intel used the FSB for inter-core communication,
and an off-die memory controller (FSB)

Now-a-days, all multi-core CPU architecture is true multi-core.
L1-L2-L3 cache sharing theory is another matter. Quite esoteric.

---

### Post by NightwishFan on 2010-03-10
The software has to support threads or 64-bit as well. If it does not, then you have the ability to run two single tasks efficiently on a dual core machine. So it is a good value to have more cores.

---

### Post by egalvan on 2010-03-10
> **ubunterooster said:**
> So I understand L-cache to be somewhat similar to RAM then, which explains some crashes.
 

Crashes due to L-cache would indicate a defective CPU.

---

### Post by ubunterooster on 2010-03-10
> **egalvan said:**
> Crashes due to L-cache would indicate a defective CPU.

Or a bad MOBO [motherboard] ? Our CPU is likely fine but our MOBO is near dead.

---

