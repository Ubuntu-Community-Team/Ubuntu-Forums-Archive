---
title: "Comp Freezes With 4GB Ram"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by fattymatty on 2008-12-06
So I've been trying to figeur out why my computer has been freezing ever since switching to ubuntu and finally figeured it out though i dont know how to rectify the situation. Even though im on ubuntu 64bit 8.04 it will not stop freezing periodicaly with 4gb of ram, it could be anywhere from 2 minutes in upto an hour before freezing. I took out one gig and runs perfect no freezing. I've run memtest for 13 hours without errors so i know its not the ram its something to do with my motherboard and linux and 4gb of ram. 

My System is
Asus V2A-VM motherboard
4X1gb ocz ram( though currently only 3 as freezes with 4)
lsh-a20 dvd burner


any thoughts of how to fix the issue

---

### Post by rev0lv3r on 2008-12-06
Could be bad ram

Do memtest on each stick of ram seperately

Make sure your bios on your mobo is the latest

I would also scale back any overclocks and check temps.

---

### Post by GW_ICO on 2008-12-14
I have almost the same problem. 
The difference is:
OS: Vista x64 SP1
<modules> 2x2GB & 2x1GB  A Data 800Mhz
2GB - ok, no matter if I use 2GB or 2x1GB
3GB - ok
4GB - freezing, all combinations tested
5GB - not tested (but I'm 100% sure that It will freeze)
6GB - freezing

---

### Post by JKBurton on 2008-12-14
On my new PC, I had to reduce "addressable RAM" in the BIOS from 4GB to 3GB before everything worked. That's a "software" equivalent of pulling out some RAM. 

I'd seen this before on Windows systems, but had never thrown 4GB at Linux before. Surprised me, but it's not like Ubuntu's needing that extra Gigabyte.

---

### Post by markbuntu on 2008-12-14
I had that problem with an old mobo but i have a new mobo with 6GB ram and have no problems at all with either hardy i386 or amd64. 

I do have problems with Intepid though, it only sees 2GB ram and only one cpu core. i hope that gets fixed soon.

---

### Post by agathian on 2008-12-14
I recall coming across a reference similar problems - please search for it.. 

i "think" the issue was bios not communicating the memory correctly to the kernel at boot time - do you correctly see the memory, before it hangs?

i "think" the workaround was to use "mem=" option during bootup... ex. "mem=4092M"  - use it at your own risk.

I would recommend looking for BIOS updates, if any, first.

---

### Post by iponeverything on 2008-12-15
I would also try running with each memory stick individuality, there just was just a case recently on this forum where memtest showed no problems but when the dude tried each stick separately, he found one stick that would consistently cause lockups.

---

