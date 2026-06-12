---
title: "keeping pendrive attached to PC safe?"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Zacinfinite on 2011-02-21
I discovered that flash drives have a limited read/write life. I keep my pendrive attached to my ubuntu PC all the time but I dont save or open any files. I dont even access the pendrive.

But as ubuntu displays the name of my pendrive (mounts automatically), is it save to keep pendrive attached? is it not reducing its life each time I switch on my PC?

Please explain the real anatomy of how things happen.

---

### Post by seawolf167 on 2011-02-21
Yes, flash drives have a limited life (finite # of writes).

However, the vast majority are formatted in FAT[32] which only writes to the flash drive when prompted. If you were to format the flash drive in say NTFS, there would now be a journaling system which gets almost constant writes (and thus reduces the life of you drive).

Flash drives are pretty advanced now in terms of read/writes, so you should essentially not have to worry about the drive wearing out (example, I have a 16 GB that I've used 4-5 times a day for the past 3 years and reformatted a dozen or so times and it has had 0 problems).

You should be able to google flash drive lifespan to find the current # of writes for most drives (and I bet it is higher than 100k for the cheapest drive - which means you'll almost certainly never reach its end lifespan before you spill water or coffee on it!)

---

### Post by Zacinfinite on 2011-02-21
But can i just keep my pendrive attacked to PC without compromising its life? if i dont read/write or open anything.

---

### Post by HermanAB on 2011-02-21
Howdy,

Don't worry, it won't wear out in your lifetime - nevermind the lifetime of the computer...

---

### Post by seawolf167 on 2011-02-21
> **Zacinfinite said:**
> But can i just keep my pendrive attacked to PC without compromising its life? if i dont read/write or open anything.

Essentially, yes.

I mean, eventually it'll wear out just like a SSD, but I ***very highly ***doubt you'll still be using that computer/flash drive when that end lifespan comes.

---

### Post by HermanAB on 2011-02-21
Howdy,

It won't wear out in your lifetime.

The parts in a computer that wear out are (in order of shortest to longest life):
1. Cooling fan
2. Electrolytic capacitors
3. Spinning disk drives

The problem with the cooling fan(s) is that when that goes, the CPU and/or  GPU may fry and then you need a new computer.

USB Memory schticks do not have any of the above components and therefore can last many, many years.  In my experience USB schticks die after going through a washer and tumble drier for the umpteenth time in my pants pocket.  So if you leave it in your machine instead of your pants pocket, then it will last much longer.

---

### Post by A_M_S on 2011-02-21
The more common flash memory type (MLC) supports 10000 write cycles.
The lifetime in a 4GB pen with daily writings of 2GB is approximately  55 years.
(4GB x 10000 writings /2GB/365days).

---

### Post by Zacinfinite on 2011-02-22
Thanks. That answers my question.

---

