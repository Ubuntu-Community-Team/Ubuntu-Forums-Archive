---
title: "Swap size"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by paddyng on 2009-10-23
What is the optimal swap size? I'm setting up a new laptop with Core 2 Duo P8600 and 4Gb RAM.

(1) I read in Ubuntu official doc (link below) that "One rule of thumb which works well is to use as much swap as you have system memory". Since I have 4Gb, swap = 4Gb.

[https://help.ubuntu.com/8.04/installation-guide/i386/apcs03.html](https://help.ubuntu.com/8.04/installation-guide/i386/apcs03.html)

(2) However further down the same install article, it says "On 32-bit architectures (i386, m68k, 32-bit SPARC, and PowerPC), the maximum size of a swap partition is 2GB". Does this apply to me?

(3) Also I read in many places elsewhere that swap should be twice the RAM.

I'm confused. Which is correct?

---

### Post by JamesParnell on 2009-10-23
i really have i idea...but i would go for option three, twice the RAM....unless you would rather have 4gb swap

---

### Post by Potters Son on 2009-10-23
Well, if you're using a 32-bit operating system, then you'll only be able to use 3 of those 4 GB's anyways... If you want to use all your ram, then you'll have to install 64-bit Ubuntu. (But in my experience, 3 GB of RAM is fine for me, and  I have fewer troubles when I use the 32 bit version).

Now, with larger amounts of RAM, it doesn't seem as if you actually need that much swap. The only time having less swap than RAM causes trouble is when you hibernate; when I only had 2 GB swap with 3 GB RAM and tried to hibernate the computer with a lot of programs running, the computer would restart from scratch instead of resuming. So, if I were you and you installed the 32 bit OS with no intention of switching to the 64, I'd partition 3 GB for swap.

---

### Post by jbrown96 on 2009-10-23
You don't need swap unless you will be using hibernate. Hibernate is probably the stupidest feature ever, so there's really no reason to use swap. 
Swap is a pagefile that is used if you run out of ram. There is literally no situation where that can happen on your system.

I have no idea why Ubuntu still recommends swap; it's just a waste of disk space. The guidelines for at least your ram is size comes from hibernate. When you put a computer in hibernate, it copies everything from ram into swap then powers off. Therefore, you could need up to your ram size to store it all in swap. But hibernate is worthless because copying up to 4GB to disk woul take 4-5 minutes (resuming would be fast). The thing is that it takes far less than 4-5 minutes to shut down and reboot your system. Shutdown or use suspend and avoid creating an out-dated swap partition.

Potters Son:
That's simply not true about how much ram you can use. Ubuntu uses PAE (physical address extension), so even with 32-bit systems it can address something like 64GB. The problem is that there is a performance penalty. There's no reason not to use 64-bit. Everything is supported now, and even if you don't get PAE performance problems, 64-bit is inheritenty faster because it uses CPU registers more effectively.

I've been using linux for three years on a variety of systems (from 512MB to 2GB). When I first started, I created swap on my 2GB machine, and it was never used. Not only that but the actual ram usage never tops ~700MB (not exactly true, see below). Even on the low-end systems, Ubuntu was smarter with the ram it uses, so they didn't use swap either. You have a 4GB system; you won't need swap. I do recommend installing preload ```
sudo apt-get install preload
``` this will put your 4GB to good use by storing commonly used files in memory, so you're not waiting on a slow HD to open commonly used files. 

Ram usage on Linux:
There is a certain amount of memory that the system must have to run. This is memory needed by the OS and currently running applications. The system will crash if it doesn't have at least this much memory (ram + swap). This is the number that never goes above ~700MB. There is also a buffer/cache. Let's say I open file A and then close it. That file was loaded into memory. Ubuntu is like hey there's nothing else that needs the memory that file A was using, so I'll leave it in memory because the user may open it again, and then it won't need to be read from the disk again. To this end, almost all of your memory is "in use"; the difference is that if something new, file B, needs memory, Ubuntu can use the memory that file A has. Preload expands on this. It will explicitly tell the system to read commonly used files into memory, so by the time you actually want to use them, they are already there and avoids the first time performance penalty from reading from the disk. It also caches files more strongly, so that Ubuntu won't drop the files from memory unless it's really necessary.

---

### Post by GimmeCoffe on 2009-10-23
Unless you are using tons of programs, and you run out of RAM (almost never happens), then swap is useless.

~GimmeCoffe

---

### Post by Paqman on 2009-10-23
As others have said, if you need to use hibernation then swap=RAM size. Otherwise with 4GB of RAM (which is way more than you'll ever use on Ubuntu) you're unlikely to dip into swap space much. Personally i'd keep a 1GB swap just in case, but that's just me.

---

### Post by tad1073 on 2009-10-23
> **Potters Son said:**
> Well, if you're using a 32-bit operating system, then you'll only be able to use 3 of those 4 GB's anyways... If you want to use all your ram, then you'll have to install 64-bit Ubuntu. (But in my experience, 3 GB of RAM is fine for me, and  I have fewer troubles when I use the 32 bit version).

Now, with larger amounts of RAM, it doesn't seem as if you actually need that much swap. The only time having less swap than RAM causes trouble is when you hibernate; when I only had 2 GB swap with 3 GB RAM and tried to hibernate the computer with a lot of programs running, the computer would restart from scratch instead of resuming. So, if I were you and you installed the 32 bit OS with no intention of switching to the 64, I'd partition 3 GB for swap.

If you want to use the 32 bit version, download the pae kernel from synaptic, it will allow all of your ram, well, 3.9 gb of it anyway, where as, the 64 bit version will allow 3.8 gb

for a while, I used 32 bit with pae kernel and was addressing 5.9 gb out of 6gb where with 64 bit I address 5.8gb out 6gb

and the rule of thumb on swap is 1.5 x amount of ram

---

