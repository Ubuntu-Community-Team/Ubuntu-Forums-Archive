---
title: "Dual boot with windows 7"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by izh34 on 2009-11-13
Hi all.
I'm kinda new here with Ubuntu and all sort of things of Linux. Doesn't know where to start. So I just post my questions here.

I am running windows 7 right now and want to try running Ubuntu 9.10 as my second dual boot. How can I do that without affecting any of partition?

This is my computer specification:
Processor: AMD Athlon 64 X2 Dual Core Processor 6000+ 3.10 GHz
Memory: 2GB
Video card: NVIDIA geforce 9500 GT
Hard Disk: 500GB, c:(60GB), d:(200GB), e:(200GB)

I see there are 32bit and 64bit Ubuntu 9.10. 

1. Which one should I install on my computer? 
2. How can I make a new partition out of my e:? cuz I have 100GB free space out of 200GB.
3. Does when I make a new partition out of e:, the data in it will gone?
4. Do I need to prepare some hardware drivers before installin Ubuntu?

and there are so many questions to ask, but I think that might suit my need to start with Ubuntu. Hope you can help me.

---

### Post by PRC09 on 2009-11-13
I would try out Ubuntu from a live cd first to make sure everything works for your system .Download the iso (I use 32 bit myself) burn to cd and boot from the cd.Then select TRY Ubuntu without making changes to my machine.It will run slower than an install but will allow you to test such things as your wireless,video,usb drives and such.That is much easier than trying to repair a fouled up install or discovering your video doesnt work...Hope this helps...

---

### Post by nothingspecial on 2009-11-13
1 64 bit
2 There is an option to do this when you install
3 Not if you use free space (theoretically, but back up everything and do a couple of defrags first)
4 No

---

### Post by the_guv on 2009-11-13
> **izh34 said:**
> 
 and there are so many questions to ask, but I think that might suit my need to start with Ubuntu. Hope you can help me.

hey [izh34]("http://ubuntuforums.org/member.php?u=954472") .. what you need, what you really really need, is:-

[LIST]
[*][The 25-Part Ubuntu KARMIC KOALA BIBLE]("http://guvnr.com/pc/karmic-koala-bible/")
[*]and this superb forum.
[/LIST]
The Karmic Bible, BTW, I wrote for Linux noobs as well as intermediates, and it covers partitioning in detail, amongst everything else you need to know to get started.

> 
1. Which one should I install on my computer? 
 2. How can I make a new partition out of my e:???: cuz I have 100GB free space out of 200GB.
 3. Does when I make a new partition out of e:, the data in it will gone?
 4. Do I need to prepare some hardware drivers before installin Ubuntu?
.. 64bit
.. refer to Bible
.. depends on how you setup but you should backup first anyway
.. no but after install navigate menu to System > Administration > Hardware Drivers

And bin Scamdows (or at least swear at it fairly regularly.)

---

### Post by Paqman on 2009-11-13
> **izh34 said:**
> 
1. Which one should I install on my computer? 


Install the 64-bit, since you have a 64-bit CPU.

> 2. How can I make a new partition out of my e:? cuz I have 100GB free space out of 200GB.

This is going to be a problem. A hard disk can normally only have four partitions. You have three already, and Ubuntu needs at least two. Luckily there is a way around the four partitions rule, using something called an extended partition. This is a sort of partition that can contain other partitions inside it, breaking the four partitions rule.

You have a few options:
[LIST=1]
[*]Create a new extended partition, and install Ubuntu inside that. You may need to shrink some other partitions to make room. You ideally need about 15-20Gb for Ubuntu, absolute minimum is 8GB. Make sure you backup and defrag before modifying any partitions.
[*]Use the [Wubi]("http://wubi-installer.org/") installer to install Ubuntu onto a virtual partition on the E:\ drive
[*]Install a new hard disk and install Ubuntu onto that
[/LIST]

> 3. Does when I make a new partition out of e:, the data in it will gone?

If you reformatted it or deleted it, yes.

> 
4. Do I need to prepare some hardware drivers before installin Ubuntu?


No. Ubuntu contains most of the drivers for your hardware already, and can download the remaining ones automatically. Running the LiveCD will tell you how well your hardware works before you commit to installing.

---

### Post by izh34 on 2009-11-13
A more questions arose from me.

I have a gigabyte tv card. Will still can play tv with ubuntu install? Do I need its driver?

I'm not oftenly online, so how can I get the best software without going online, like having install restricted codec and media to play my mp3, avi, flash etc?

---

