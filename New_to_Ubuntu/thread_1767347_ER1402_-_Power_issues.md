---
title: "ER1402 - Power issues"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by Capt_Spaulding on 2011-05-25
Hey all,

Recent convert to Ubuntu, so consequently know sod all. Apologies in advance if this is posted in the wrong place, or utterly stupid!

I have a brand new ER1402 

[http://www.emachines.com/products/products.html?prod=ER1402-05](http://www.emachines.com/products/products.html?prod=ER1402-05)

I installed Ubuntu 11.04 from the downloadable CD option.

All works brilliantly - however,** I cannot restart, shutdown, hibernate, sleep**, etc. Basically, if I choose any of the above, from the top bar, or via various commands in terminal, the machine simply hangs, gives me a random colour screen (generally a purpley)... and the only way out of this is to hold the power button until the machine shuts down.

I've checked the bios which seems to be up to date.

Please help anybody! :confused:

---

Worth noting, I removed any previous OS when I acquired the machine. There is now only one partition on the internal drive, and that is Ubuntu!

---

### Post by jkurtisr32 on 2011-05-25
> **Capt_Spaulding said:**
> Hey all,

Recent convert to Ubuntu, so consequently know sod all. Apologies in advance if this is posted in the wrong place, or utterly stupid!

I have a brand new ER1402 

[http://www.emachines.com/products/products.html?prod=ER1402-05](http://www.emachines.com/products/products.html?prod=ER1402-05)

I installed Ubuntu 11.04 from the downloadable CD option.

All works brilliantly - however,** I cannot restart, shutdown, hibernate, sleep**, etc. Basically, if I choose any of the above, from the top bar, or via various commands in terminal, the machine simply hangs, gives me a random colour screen (generally a purpley)... and the only way out of this is to hold the power button until the machine shuts down.

I've checked the bios which seems to be up to date.

Please help anybody! :confused:

---

Worth noting, I removed any previous OS when I acquired the machine. There is now only one partition on the internal drive, and that is Ubuntu!

Your computer model has been certified for the newest release of Ubuntu, but from what I can tell, it is only the x86 version. Are you running the 64-bit or 32-bit version of Ubuntu?

Depending on your system specs, I would consider trying 32-bit, and seeing if that helps. I've often found that using 32-bit Ubuntu can solve some issues that I've had with hardware on 64-bit. Some might consider that solution to be for bitchez, but if it's an easy fix, and if you have lower system specs, then whatevs.

-Kurt

---

### Post by Capt_Spaulding on 2011-05-25
Thanks ever so much for replying! At wit's end here...

I've tried 'file /sbin/init' and it reports I'm running 32 bit... 

Any other ideas? No matter how crazy :)

---

### Post by jkurtisr32 on 2011-05-25
> **Capt_Spaulding said:**
> Thanks ever so much for replying! At wit's end here...

I've tried 'file /sbin/init' and it reports I'm running 32 bit... 

Any other ideas? No matter how crazy :)

Well, I took another look. It seems that you are not alone in this issue. A quick Google search revealed that this is a bug that was reported just earlier this month (on May 12th):
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/781911](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/781911)

It seems that a few people have had this issue, so I would assume that the developers are working on a fix. That really sucksss, I hate issues like these.

-Kurt

---

### Post by Capt_Spaulding on 2011-05-25
Poooh!

I saw that too - was wondering if there was any clever ideas you guys might have.

So does it look like we just have to wait until Ubuntu developers write a fix? What a bummy start to my Ubuntu experience! :(

---

### Post by jkurtisr32 on 2011-05-25
> **Capt_Spaulding said:**
> Poooh!

I saw that too - was wondering if there was any clever ideas you guys might have.

So does it look like we just have to wait until Ubuntu developers write a fix? What a bummy start to my Ubuntu experience! :(

I know, dude. I've had issues like this before, where the problem is some kind of awkward hardware problem. I just kept looking for updates, and eventually it magically worked.

By the way, if you do plan on sticking with Ubuntu exclusively, and if you haven't done so already, I would look into getting a refund for your Windows version (if EMachines made you select a version, and if it came preloaded with Windows). I think that manufacturers typically will give you money back if you don't plan on using the Windows software. Just sayin'

-Kurt

---

### Post by Capt_Spaulding on 2011-05-25
Hey buddy,

Thanks for the help and advice. Unfortunately, the machine came with a version of Linux installed (it was cheaper than the Windows 7 version).

Do you have any idea how long this kind of problem is liable to wallow before an update is released? Should I run with an alternative OS until then?

Cheers

---

### Post by jkurtisr32 on 2011-05-25
> **Capt_Spaulding said:**
> Hey buddy,

Thanks for the help and advice. Unfortunately, the machine came with a version of Linux installed (it was cheaper than the Windows 7 version).

Damn, I didn't know that manufacturers were offering preloaded Ununtu. Shows how long I've been out of the market for computers.

> 
Do you have any idea how long this kind of problem is liable to wallow before an update is released? Should I run with an alternative OS until then?

Cheers

I don't know how long it will take for them to fix it. I'm sure it depends on how many other people are reporting the issue and how easy it is to fix.

In the meanwhile, I would NOT recommend switching OS. I mean, if I were you, I would consider this a minimal issue, especially given your hardware. I mean, hard poweroffs aren't going to kill your machine or anything. But, hell, I would just leave the thing on all the time. Just read that the power cost per year of this machine is less than $7 on average:
[http://reviews.cnet.com/desktops/emachines-er1402-05/4505-3118_7-34123068-2.html](http://reviews.cnet.com/desktops/emachines-er1402-05/4505-3118_7-34123068-2.html)
I would just leave it all the time, and I couldn't imagine that it would be much more expensive ($14, even $21 per year?).

-Kurt

---

### Post by Capt_Spaulding on 2011-05-25
Cheers mate.

When I said Linux, it wasn't the Ubuntu flavour... I've forgotten exactly which!

Good point re energy and prices. ;)

I've also reported the bug, so now I'll sit back and start my stopwatch.

Cheers for support.

;)

---

### Post by Capt_Spaulding on 2011-05-30
In case any other poor sods suffer this problem... I found a solution!

Only took 4 flippin' days!

See here :

[http://ubuntuforums.org/showthread.php?t=1694262&page=2](http://ubuntuforums.org/showthread.php?t=1694262&page=2) (see TimGood's post)

and 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103)

Phew.

---

