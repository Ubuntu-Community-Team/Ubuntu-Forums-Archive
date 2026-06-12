---
title: "Gateway GT5628"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by stevemcb263 on 2009-06-08
I have been given a Gateway GT5628 running Vista.  

It has an Intel Core 2 Quad processor Q6600, a 500Gb SATA II hard drive and an NVidia GeForce 8500GT video card.

What Ubuntu Distribution should I use on this machine?  I wanted to dual boot the machine (Vista and Ubuntu).  I tried an i386 9.04 install disk I had (as a LiveCD), but it loses the keyboard and mouse after a few seconds and the screen just hangs as it's drawing the panels - so I'm assuming it's the wrong distro.

Any suggestions?  Does anyone have any experience installing Ubuntu on a GT5628?

Steve

---

### Post by HappyFeet on 2009-06-08
Sounds like you have a very linux unfriendly computer. You could try ubuntu 8.10 or 8.04

If those don't work, you will have to abandon ubuntu all together and try a different distro such as Mandriva One, or OpenSuse. Perhaps even Fedora (the new release comes out tomorrow).

---

### Post by stevemcb263 on 2009-06-08
Thanks for the response.

Do you think it would make a difference if I tried the 64 bit distribution?

---

### Post by CJ Master on 2009-06-08
Try MEPIS linux, I've heard it has nice hardware support.

Don't try the 64 bit distribution unless you know for sure that you have a 64 bit processor.

---

### Post by reeseslover531 on 2009-06-08
that is a 64-bit cpu (I have one myself, and I run 64 bit) but unless you have 4gb or more of ram there is no point, and I am pretty sure it won't help your problems.

---

### Post by anewguy on 2009-06-08
The computer specs should be fine except for 1 thing - the video.  I had a similar config on a computer I recently had to sell - it worked fine in 8.04 and 8.10, but I never did upgrade it to 9.04.  I've seen various posts here about problems with video drivers now - I just used envyng when I had that machine, but maybe the driver support is gone from nVidia's driver package or something now.  I'd do a google search with

ubuntu 9.04 nvidia 8500GT video driver

and see what turns up.  There may be some guidance out there.  Personally, I would download and burn the 8.04 LiveCD and try running Ubuntu from the it first and see how it goes.  If it's acceptable to you, you can then install from that CD.  If not acceptable, at least you'll have an idea what doesn't work and therefore be able to do more searching to see if there is either a fix or if a different distribution might be right for you.  There are also known issues in 9.04 when you have certain Intel chipsets - that's why I would try 8.04.

Dave :)

EDIT:  This may be of interest, and why to try 8.04 instead:

[http://www.blog.arun-prabha.com/tag/nvidia/]("http://www.blog.arun-prabha.com/tag/nvidia/")

---

### Post by sandyd on 2009-06-08
> **stevemcb263 said:**
> I have been given a Gateway GT5628 running Vista.  

It has an Intel Core 2 Quad processor Q6600, a 500Gb SATA II hard drive and an NVidia GeForce 8500GT video card.

What Ubuntu Distribution should I use on this machine?  I wanted to dual boot the machine (Vista and Ubuntu).  I tried an i386 9.04 install disk I had (as a LiveCD), but it loses the keyboard and mouse after a few seconds and the screen just hangs as it's drawing the panels - so I'm assuming it's the wrong distro.

Any suggestions?  Does anyone have any experience installing Ubuntu on a GT5628?

Steve
Those specs are way over kill. like using a jet fighter to kill a fly.

---

### Post by anewguy on 2009-06-08
Yeah, he has overkill, but it should work.  There are only 2 things I can see that might be a problem for 9.04 - the video like I mentioned and perhaps if it has certain Intel chipsets, as I have read that certain Intel chipsets have problems with 9.04.  That's why I recommended they try 8.04.  If 8.04 works, then they can always try the 64-bit version if they want.

Any other ideas to help them out?

Thanks!
Dave :)

---

### Post by stevemcb263 on 2009-06-09
Thanks for all the inputs.

It loaded and ran Ubuntu 7.1 just fine.  The frame rate on glxgears in 7.1 was only about 256, so I imagine I'll have to load the NVidia proprietary drivers to get a decent speed out of the video card, as well as appropriate screen resolution.

Maybe it was just a bad burn on the 9.04 CD.

I just tried an 8.04 CD and it had the same reaction - lost the keyboard and mouse.  I'm going to play with it in my spare time and see if I can get it working.

Anyway, It's good to know someone has successfully loaded a flavor of Ubuntu on a asimilar machine, so I'll keep working on it.

Thanks!
Steve

---

### Post by anewguy on 2009-06-09
> **stevemcb263 said:**
> Thanks for all the inputs.

It loaded and ran Ubuntu 7.1 just fine.  The frame rate on glxgears in 7.1 was only about 256, so I imagine I'll have to load the NVidia proprietary drivers to get a decent speed out of the video card, as well as appropriate screen resolution.

Maybe it was just a bad burn on the 9.04 CD.

I just tried an 8.04 CD and it had the same reaction - lost the keyboard and mouse.  I'm going to play with it in my spare time and see if I can get it working.

Anyway, It's good to know someone has successfully loaded a flavor of Ubuntu on a asimilar machine, so I'll keep working on it.

Thanks!
Steve

Just thought of something - are your keyboard and mouse USB?  Either way, check the BIOS on your system and be sure you have the option enabled for "legacy devices".  I know it will show different for each BIOS, but it should be something along those lines.  Try enabling it and see if it helps.

Dave :)

---

### Post by stevemcb263 on 2009-06-09
Well, here's a lesson for you, boys and girls!  Check the integrity of your freshly burned CD BEFORE you try to run it on your system! 

Don't just do the MD5SUM and assume it will work!

More later, after I burn a new CD!

---

