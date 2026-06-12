---
title: "I7 Install for 9.04"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by micklerr@gmail.com on 2009-09-23
Hello - simple question hopefully.

Bringing home an I7 box today. Specs:

Intel core i7 920 2.66ghz 4.8gt/lga1366 8mb cache on a MSI x58 Paltinum SLI. 6GB RAM.

Any issues with x64 installer for 9.04 that I should know about? I went to download it and the file is an amd64.iso - not sure if that's incompatible with the Intel I7? Is that the right distro that I need? Etc etc?

Any and all advice appreciated. I use Ubuntu on a 32bit platform just swimmingly. 
Thanks!

R

---

### Post by wizard10000 on 2009-09-23
I ran 9.04 (and now 9.10) on an i7 box.  AMD64 is the distro you need and it'll work just fine.  You'll find that temperature sensors in 9.04 don't work unless you compile lm-sensors from source and install but other than that everything works as advertised.

Have fun -

---

### Post by nhasian on 2009-09-23
congrats on your new rig.  I'm jealous!  I'm still on an original Pentium D 3.2Ghz.  Waiting till the new 32nm Intel Processors come out this Q4 before getting a new system.  The I7 core has been out about a year now so there are no big issues that i'm aware of.  If your motherboard has the new P55 intel chipset, there are a few issues with that though:

[http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=4](http://www.phoronix.com/scan.php?page=article&item=intel_p55&num=4)

> On some test runs with the Phoronix Test Suite the Lynnfield processors would run very well, but when running the tests again just seconds later, the performance results would be wildly and severely impaired. This had happened with both the Core i5 750 and Core i7 870. When facing these problems, Enhanced Intel SpeedStep Technology (EIST) was disabled, and we tried a few other tweaks, but the problems persisted with both Ubuntu 9.04 and the Ubuntu 9.10 development snapshot.

But you dont need to worry about that as your motherboard uses last year's X58 intel chipset.

---

### Post by micklerr@gmail.com on 2009-09-29
Thanks yall - really appreciate the information!

It, in fact, installed cleanly on the I7 and has been fantastic. What used to take me a day and a half in processing files in a VM now just takes a few hours. Amazing! It's working great...!

Best wishes - 
R

---

### Post by Prometheus7 on 2009-10-09
I am using an i7 860 with a dp55kg intel mb and 9.04 did not work for me. Specifically, my ethernet port was not recognized. To the best of my knowledge, you have to step up to the latest kernel (2.6.31) or update to 9.10 Karmic in order to get everything working.

BTW, those issues that Phoronix reported were later taken back in a later review. Phoronix had been given an early version of the BIOS. If you update your BIOS you should not have those issues.

---

### Post by advocate 21 on 2009-10-12
im confused on that too; i have the 920 core as well.. however, for the time, you have to use AMD64 packages...

---

### Post by LowSky on 2009-10-12
> **advocate 21 said:**
> im confused on that too; i have the 920 core as well.. however, for the time, you have to use AMD64 packages...

AMD was the creator of 64bit processors. intel uses AMD instruction set, regardless of what intel calls it, your running AMD64. That is why its called that and most likely will be called that for as long as 64bit computing is used.

It works just as well on AMD or intel, just like both companies made x86 chips and intel owned the rights to that.

---

