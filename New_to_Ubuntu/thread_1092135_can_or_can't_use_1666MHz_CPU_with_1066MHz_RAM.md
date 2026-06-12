---
title: "can or can't use 1666MHz CPU with 1066MHz RAM??"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by powel212 on 2009-03-10
Hi

I want to upgrade my processor.

My motherboard supports up to 1666mhz processor

but 

only supports maximum DDR2-1066MHz RAM

My question is if I buy a 1666MHz CPU will I actually see a performance improvement because my ram speed is limited to 1066MHz

I could buy

intel 3.0Ghz 1066MHz CPU

or

Intel 3.0 GHz 1666MHz CPU

But because my RAM is limited to 1066MHz will there be significant performance increase with the more expensive chip? The price difference is substantial but I don't mind if it will perform well.

Motherboard is ASUS P5K-E

Thanks

Powel

---

### Post by skymera on 2009-03-10
With faster RAM you'll see little to no improvement on Ubuntu.

Your CPU bus speed is 266MHz while your RAM is 533MHz 
So your RAM is more than fast enough.

But yes, as long as your motherboard supports it you can use the fastest RAM and compatible processor

When you say "1666MHz CPU". Do you mean clock speed or bus speed?
Bus speeds are typically 1066, 1333, 1600mhz

---

### Post by 3rdalbum on 2009-03-10
RAM speed and processor speed are not the same. The CPU will work just fine. Incidentally, if you have less than a 1.6GHz CPU, it's doubtful that you'd have 1066MHz RAM - you probably have 667 or 800MHz RAM.

I don't know what you mean by "intel 3.0Ghz 1066MHz CPU". If it's 3GHz, it's 3GHz not 1066MHz. I don't know what you mean by that second number. If you are buying a new CPU, you need to make sure that it fits into your current motherboard socket - I imagine the P5K-E motherboard has an LGA775 socket which means you want a Core 2 CPU, not a Xeon processor as that won't work.

---

### Post by bailbath on 2009-03-10
1066mhz is the front side bus same as 667 or 800mhz

---

### Post by louieb on 2009-03-10
Vista and XP use  NTLDR. Don't know thats its better. I think NTLDR uglier and harder to configure than GRUB. Anyway heres one way it can be done [IDBS WinGrub (NTLDR) and Ubuntu]("http://users.bigpond.net.au/hermanzone/p9.html")

---

### Post by bailbath on 2009-03-10
cpu
intel Socket 775 Core™2 Quad/Core™2 Extreme/Core™2 Duo/Pentium® Extreme/Pentium® D/Pentium® 4 Processors
Compatible with Intel® 05B/05A/06 processors
Support Intel® 45nm CPU
*This motherboard supports FSB 1333/1066/800
** Please update the latest BIOS to support Intel 45nm CPU 
Ram
4 x DIMM, Max. 8 GB, DDR 1600*/800/667 Non-ECC,Un-buffered Memory
Dual Channel memory architecture
*The chipset officially supports the memory frequency up to DDR2 800MHz. Tuned by ASUS Super Memspeed Technology, this motherboard natively supports up to DDR2 1066MHz
Please refer to [www.asus.com](www.asus.com) or user manual for Memory QVL.


This is from Asus own website might be worth trying a hardware forum you may get better answers.
Ian

---

### Post by powel212 on 2009-03-10
Thanks for all the great feedback. 

Skymera - sorry i wrote the wrong number
I misspoke when I said 1666MHz - You are right it is 1600mhz. 

Bailbath
The ASUS website says this motherboard natively supports  RAM to 1066mhz.
Do you know what that means "Natively"

I currently have a 2.66ghz intel CPU and 6G of DDR2-800mhz.

The machine rocks but I want to be able to process video more quickly.

I went to the Tech shop today after work and the tech guy there said that if i run a 1333mhz CPU with 1066mhz RAM then the RAM speed is in effect reducing the potential processing power of the CPU.

It seems I can't get a much better CPU for my Motherboard. So it seems if I want to go faster I need to get a core i7 and new motherboard. But Those chips and boards are currently prohibitively expensive so I will sit on my hands for a few months and see what happens. I expect with the recession and intel laying off thousands of people there will be few advances in CPU technology any time soon. So, i'll probably be sitting on my hands for a while.

Has anyone heard if the next Ubuntu will have 64bit intel compatibility?

Powel

---

### Post by bailbath on 2009-03-10
It already has 64 bit support has for some time you just use the amd64 instead of i386 ubuntu to install.
I think you will get better answers at this site- [http://www.phoronix.com/scan.php?page=home]("http://www.phoronix.com/scan.php?page=home") for your hardware questions.
The motherboard supports 1066 memory as is but is capable of overclocking. Again go to the above website. They have a forum too- [http://www.phoronix.com/forums/]("http://www.phoronix.com/forums/")
All the best
Ian

---

### Post by powel212 on 2009-03-11
I felt it noteworthy to mention that I changed over to 64Bit Ubuntu yesterday and the speed increase is really quite remarkable. Thanks so much for telling me it is now possible to run 64Bit Ubuntu with my intel chip.

Under 32Bit it could only recognize 3.4G of my RAM

Under 64Bit it recognizes all 6Gigs.

Powel

---

