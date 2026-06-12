---
title: "trying to run Xubuntu Live CD on Thinkpad 1200"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by padredenny on 2008-12-05
I'm trying to get the Xubuntu Live CD to run on my Thinkpad i Series 1200 - 700Mhz, 128MB RAM, 20 GB hard drive.

I get through the rolling progress bar, then to the end of the expanding progress bar. Then the system displays some garbled screens, and then the screen goes black.

I've read some other threads that recommend adding various things to the boot options: vga=792, acpi=force irqpoll, noapic nolapic acpi=off. None of these seem to help.

I would like to eventually do an install, but I really want to run the Live CD first so I can make sure I can get everything working (screen resolution, wireless internet etc.) before I get rid of Windows ME (!) forever.

Any help would be greatly appreciated. Thanks.

---

### Post by snowpine on 2008-12-05
Hi and welcome to the forums! You don't have enough ram to run the live cd, unfortunately. I would recommend upgrading to at least 256mb, preferrably 512mb for best result.

You may be able to install using the Xubuntu alternate CD, which uses a text based installer instead of a live session. Frankly I have never tested it on a computer with so little ram, so I can't say 100% it will work.

The only two Live CDs I know of that will work with 128mb are Puppy and DSL. 

Good luck!

---

### Post by padredenny on 2008-12-05
Thanks. But this Thinkpad (i Series 1200 1161), I'm told, can't be upgraded past 192MB RAM. Which is strange because there are vendors online selling 256 and 512 modules for this specific model. Old computers, it appears, are a minefield for non-hardware people like me.

I would try the alternate install, but I don't want to wipe out my old OS until I know Xubuntu (or whatever) will work. As crappy as Windows ME is, at least it runs, and I can access the internet from it.

I managed to get Damn Small Linux running from a CD, but it's really ugly.

The sad thing is, this computer is old, but it's a beautiful tank. I was hoping that Linux or something would give it a new lease on life.

---

### Post by snowpine on 2008-12-05
20gb hard drive is big enough that you can set up a "dual boot" between Windows and Xubuntu. Are you familiar with this process? If Xubuntu doesn't work, you can delete its partition and re-biggen your Windows partition. :)

---

### Post by padredenny on 2008-12-05
I understand the partitioning and dual boot process, I've just never done it before. Will the alternate install CD do those setups for me, or do I need other programs?

Thanks for your help.

---

### Post by mister_pink on 2008-12-05
The alternate CD will do that for you, its just not quite so easy. 

I would guess that the easiest thing to do would be to create the partitions you need (shrink windows, create a root(/) and swap partition at least with another live CD that works, then use the alternate cd. 

I've only ever used the alternate cd on a blank hard disk, but it can't hurt to boot it up and see if it will actually do this automagically. If it doesn't, cancel and do it yourself.

---

