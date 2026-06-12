---
title: "Question about bootloaders."
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Dullstar on 2009-10-11
Even though I know what I'm doing on Linux, I do get a few questions every once and a while.  I would like to know if I can switch from my current bootloader (the one that came with Windows) to GRUB without harming anything.

---

### Post by eagle416 on 2009-10-11
as far as I knew installing ubuntu did exactly that automatically. The answer is yes, you can switch your bootloader and all the partitions are safe, and furthermore I don't believe the windows bootloader even lets you start ubuntu at all, so you would have to switch anyway.

---

### Post by Dullstar on 2009-10-11
All pictures of GRUB look totally different from mine.
I can snap a photo if needed.

---

### Post by eagle416 on 2009-10-11
please do. Is it possible that you simply have a theme attached? Where did you get your version of grub?

---

### Post by Dullstar on 2009-10-18
Um, I REALLY don't think this is grub...

Look at this.

---

### Post by Dullstar on 2009-10-18
By the way, I just have whatever Wubi put on there, but I'm guessing it did nothing except make Ubuntu bootable in the Windows bootloader.  Although I'd love to have GRUB, I think it looks nice, so if anyone can tell me how to get this.

---

### Post by NoaHall on 2009-10-19
Download and burn the SuperGRUB disk. Run it, and then it will install GRUB for you.

---

### Post by Incendia on 2009-10-19
> **Dullstar said:**
> By the way, I just have whatever Wubi put on there, but I'm guessing it did nothing except make Ubuntu bootable in the Windows bootloader.  Although I'd love to have GRUB, I think it looks nice, so if anyone can tell me how to get this.

Wubi uses Windows Bootloader.
Try and install Ubuntu the standard way :] you get more performance, apparently.

---

### Post by Mark Phelps on 2009-10-19
> **Dullstar said:**
> By the way, I just have whatever Wubi put on there, but I'm guessing it did nothing except make Ubuntu bootable in the Windows bootloader.  Although I'd love to have GRUB, I think it looks nice, so if anyone can tell me how to get this.

Actually -- it did a LOT more than that.  It installed Ubuntu "inside" MS Windows in a special file on your hard drive that Ubuntu treats as a partition, and added a line to your boot.ini file that presents the option to boot Ubuntu when the MS Windows boot menu gets displayed.

If you install GRUB, you will have to move Ubuntu to its own partition for that to work.  Presently, you're using GRUB4DOS to do the boot from files inside the MS Windows partition.

---

### Post by Dullstar on 2009-10-19
I will do a fresh install of Karmic.

---

### Post by Dullstar on 2009-10-20
Once I get GRUB installed, will the W word (I hate Windoze) still be bootable (sadly, I need it sometimes.  Which really sucks.)?

---

### Post by Sarmacid on 2009-10-20
Yes, usually grub checks out your system for installed OSs and adds them to the list.

---

### Post by Dullstar on 2009-10-21
And I was told that SPORE functions in WINE perfectly, if this is true, this could require the HARD DRIVE ERASER!  W00T!  *lol*

---

### Post by Incendia on 2009-10-22
> **Dullstar said:**
> And I was told that SPORE functions in WINE perfectly, if this is true, this could require the HARD DRIVE ERASER!  W00T!  *lol*

Yes it does. 

**Description**
Version 1.x
Selected Test Results (selected in 'Test Results' table below)

**What works**
Everything

**What does not**
Nothing

**What was not tested**
Space

**Additional Comments**
Had to change light settings.

> [CENTER]Please refer to [http://appdb.winehq.org](http://appdb.winehq.org) for Wine program compatibility questions.[/CENTER]

:]

---

