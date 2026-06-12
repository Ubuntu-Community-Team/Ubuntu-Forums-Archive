---
title: "Installation troubles"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by e2wen~* on 2009-05-09
Hi, I'm sorry if this is posted in the wrong topic but I don't know where else to put it up.

I tried to install Ubuntu both as dual OS with WinXP and on its own but twice I get the same message when it restarts after installation is complete.

[IMG]http://img.photobucket.com/albums/v469/ferum/DSC00586.jpg[/IMG]

What is this supposed to mean?

I'm currently back on WinXP because I have only one computer to try it out on.
Where could I make a mistake to get this error? I'm quite sure I followed every step as instructed.

---

### Post by jerrrys on 2009-05-11
is this the live cd??

---

### Post by jacksinn on 2009-05-11
It looks like it can't recognize your HDD. Did you have any external HDDs plugged in when you did an install (perhaps it's looking for an external HDD)? 

Also, I'm a big fan of WUBI for new Ubuntu users. To use it, create a disk of the latest distro and insert it into your CD drive when you are booted into Windows. You'll be able to install Ubuntu much like you would with any other program and can uninstall it via Add/Remove programs. When you rebbot, you'll get a boot menu (default selection is Windows). This helps those new to Ubuntu try the distribution in a way more flexible than using live cds and with less damage potential than trying to setup a true dual boot via partitioning.

---

### Post by e2wen~* on 2009-05-12
jerrrys, yes, I installed it from a live CD.

jacksinn, I didn't have an external HDD plugged in. I managed to find out from a friend that Ubuntu doesn't run well on AMD processor, could that be a problem?

As for "create a disk of the latest distro", it's still a little confusing for me. The live CD I have is of Ubuntu 8.10, can I install it as WUBI too? Will it run slow if I use WUBI instead?

Thank you guys for your willingness to help out!

---

### Post by caravel on 2009-05-12
> **e2wen~* said:**
> I managed to find out from a friend that Ubuntu doesn't run well on AMD processor, could that be a problem?
That is incorrect.  Linux runs fine on AMD CPUs.  In fact there is an Athlon64 specific Linux kernel.

---

### Post by Kevbert on 2009-05-12
Welcome to Ubuntu.
AMD processors aren't a problem with Ubuntu. I'm writing this email on an AMD64x2 PC and also have a single Athlon 900Mhz PC running 9.04 Jaunty Jackalope.
Questions - Did you burn the CD yourself ?
Have you run memtest86+ from the first menu that is displayed when you run up the CD ?
What are your computer specs ? (RAM,video card etc).
Prior to running the install Ubuntu did you defrag and [[COLOR="Red"]chkdsk[/COLOR]]("http://en.wikipedia.org/wiki/Chkdsk") the hard disk via Windows ?

---

### Post by Jimmyfj on 2009-05-12
> **e2wen~* said:**
> jerrrys, yes, I installed it from a live CD.

jacksinn, I didn't have an external HDD plugged in. I managed to find out from a friend that Ubuntu doesn't run well on AMD processor, could that be a problem?

That is simply NOT true - Ubuntu runs very good indeed on AMD processors. Your problem is not your hard drive nor your CPU - Is your graphics card an ATI card? If so your best served by installing from the alternate install cd.

---

### Post by Bölvaður on 2009-05-12
> **e2wen~* said:**
> As for "create a disk of the latest distro", it's still a little confusing for me. The live CD I have is of Ubuntu 8.10, can I install it as WUBI too? Will it run slow if I use WUBI instead?

9.04 is the latest one. Hence the number  (4th month of 2009). I am a big hater of Wubi as it installs it self inside windows as a file, which means you will have to defragment your disk before installing. It also means that you have slower file system but in all honest you will not notice that much difference. With Wubi you will not get grub as boot loader, and hence will not be able to choose how ubuntu is suppose to boot if you need to use some special things. Other than that it is great, so in average it might be better for you.


The problem you are having is difficult... are you able to see the partition and identify files on it from a live cd? Just to make sure your hard disk might not just be faulty.
I would guess something like that is the problem as the error is that it doesnt find the partition you installed ubuntu on (assuming it is the first partition on the first hard disk you got)

---

### Post by Bölvaður on 2009-05-12
> **Jimmyfj said:**
> That is simply NOT true - Ubuntu runs very good indeed on AMD processors.


There was limited number of motherboards that was a problem some time ago...... that's where the misunderstanding is coming from. So dont read cpu but motherboard.

---

### Post by e2wen~* on 2009-05-12
> **Kevbert said:**
> Did you burn the CD yourself ?
I bought the CD from a local Ubuntu community, which I'm guessing they burnt the CD themselves.

> **Kevbert said:**
> Have you run memtest86+ from the first menu that is displayed when you run up the CD ?
I did.

> **Kevbert said:**
> What are your computer specs ? (RAM,video card etc).

AMD Turion 64 Mobile Technology MK36 (2.0 GHz, 512KB L2 cache)
ATI Radeon Xpress 1100
80GB HDD
DVD-Super Multi double Layer
1GB DDR2

> **Kevbert said:**
> Prior to running the install Ubuntu did you defrag and [[COLOR=Red]chkdsk[/COLOR]]("http://en.wikipedia.org/wiki/Chkdsk") the hard disk via Windows ?Yes.

---

### Post by e2wen~* on 2009-05-12
> **caravel said:**
> That is incorrect.  Linux runs fine on AMD CPUs.  In fact there is an Athlon64 specific Linux kernel.
> **Kevbert said:**
> AMD processors aren't a problem with Ubuntu. I'm writing this email on an AMD64x2 PC and also have a single Athlon 900Mhz PC running 9.04 Jaunty Jackalope.
> **Jimmyfj said:**
> That is simply NOT true - Ubuntu runs very good indeed on AMD processors. 
> **Bölvaður said:**
> There was limited number of motherboards that was a problem some time ago...... that's where the misunderstanding is coming from. So dont read cpu but motherboard.
Sorry for not getting my facts right before asking. 
And thanks, Bölvaður, for clearing the misunderstanding.


> **Jimmyfj said:**
> Your problem is not your hard drive nor your CPU - Is your graphics card an ATI card?
As mentioned earlier, I do have a ATI graphic card.

And yes, I did notice some graphic glitch but ignored it because I didn't think graphic card would be a problem.
> **Jimmyfj said:**
> If so your best served by installing from the alternate install cd.
Which alternate install cd do you mean?

---

### Post by e2wen~* on 2009-05-12
> **Bölvaður said:**
> Other than that it is great, so in average it might be better for you.
I guess I could try starting off with WUBI because I'm not a heavy user.
Is WUBI available on 8.10? Do I have to get a new copy to use WUBI?


> **Bölvaður said:**
> are you able to see the partition and identify files on it from a live cd? Just to make sure your hard disk might not just be faulty.
I would guess something like that is the problem as the error is that it doesnt find the partition you installed ubuntu on (assuming it is the first partition on the first hard disk you got)
Yes, I should have mentioned that earlier, silly me.
There were a few times I can't go on with installation because it cannot detect the partitions on my hard disk.
I would quit and try again until it gets through that part.
Then I'm stuck at the image I posted up there.
I always install in on the first partition of the only hard disk intact to my laptop.

---

