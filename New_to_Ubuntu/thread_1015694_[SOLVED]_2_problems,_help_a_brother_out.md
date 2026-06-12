---
title: "[SOLVED] 2 problems, help a brother out"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by trigity on 2008-12-19
1st. upon restart I get a msg that say's,
Blah, Blah,
PXE-E61: media test faliure, check cable
PXE-M0F: ext pxe rom
operating system not found 

my acer runs fine from a cold start after sudo shutdown -h now 
But, sudo shutdown -r now; re: 1st problem

2nd. Places, Home folder, opens archive mgr with a secondary window inside that say's, could not open "trigity" archive not supported.

---

### Post by Michael.Godawski on 2008-12-19
> **trigity said:**
> 1st. upon restart I get a msg that say's,
Blah, Blah,
PXE-E61: media test faliure, check cable
PXE-M0F: ext pxe rom
operating system not found 

my acer runs fine from a cold start after sudo shutdown -h now 
But, sudo shutdown -r now; re: 1st problem

2nd. Places, Home folder, opens archive mgr with a secondary window inside that say's, could not open "trigity" archive not supported.

PXE-E61: media test faliure, check cable: you need a crossoever cable, not a usual ethernet cable
just a guess

---

### Post by hyper_ch on 2008-12-19
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by trigity on 2008-12-19
Sorry all I'm still getting used to the edicate. I'm green as a blade of grass...I did mean to make anybody, offend anyone..

---

### Post by Kellemora on 2008-12-19
Hi tigity

As you are booting up, if you have boot screen text turned on that is.

Are you seeing an
ATA (whatever) followed by [DRDY] ?????

It could be you need to unplug your hard drive and reseat the cables again.  Or the drive is going south!

If you don't see the boot up text, you can
```
gksu gedit /boot/grub/menu.lst
```
Then remove the words "Quiet" and "Splash" from behind the word "ro" in your bootload line.
Then when you boot up, you will see all the STUFF that is loading and if each thing is getting an OK or showing a problem.

TTUL
Gary

---

