---
title: "Dell mini horrible tearing when moving windows?"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by turbodellmini on 2009-08-07
Last night I got a wild hair and decided to dump windows xp on my dell mini in favor of ubuntu NBR.  The first thing I noticed was that when ever I move a window around it tears horribly.  Is this a normal expierence in Linux?  What can I do to get smooth movement like in Windows?  Is poor graphics performance like this a normal expierence?

---

### Post by Paddy Landau on 2009-08-07
What precisely do you mean by "tears around"?

There are graphics effects that you can turn off easily.

---

### Post by turbodellmini on 2009-08-07
Haha sorry,

What I meant is that when I had Win XP installed and I moved a window or scrolled down in firefox the movement was smooth, however in ubuntu when I do the same there are horrible tear marks, as if the refresh rate is really low.  But in display settings it says 60Hz.  I tried this with both desktop effects on and off and it seems to make no difference, however with them on it seems more pronounced.  

I read some threads on this, but none ever seem to be resolved.

Thanks,

Matt.

---

### Post by Paddy Landau on 2009-08-07
It sounds as though your graphics card is not fully supported.

I'm no expert on graphics, but if you post your RAM size, your computer make and model, and your graphics card make and model, I suspect that someone else on this forum would be able to make sense of it. Also tell us what version of Ubuntu you're using.

---

### Post by turbodellmini on 2009-08-07
Thanks Paddy,

I'm currently running Ubuntu Netbook Remix 9.04 on a Dell Mini 9 with the Intel GMA945GME.

---

### Post by Paddy Landau on 2009-08-07
> **turbodellmini said:**
> Thanks Paddy,

I'm currently running Ubuntu Netbook Remix 9.04 on a Dell Mini 9 with the Intel GMA945GME.
Hmm, the Intel 945 sometimes does cause problems with Linux.

Does your Live CD (or USB) have this problem?

---

### Post by turbodellmini on 2009-08-07
> **Paddy Landau said:**
> 
Does your Live CD (or USB) have this problem?


Yes, I've had this problem since I booted up from the live USB.  Also, I just tried Linux Mint (I've heard of this solving some tearing problems for other people) and It tears the same. 

I'm kind of thinking there might not be a solution for this?:(

---

### Post by novafluxx on 2009-08-07
The UNR *should* work fine with the Mini 9.

There is a Dell remix of Ubuntu that you might consider trying as well, if you're interested:

[http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)

This is supposed to have all the needed drivers for the Mini 9.

How much RAM/Memory does your Mini 9 have?

---

### Post by turbodellmini on 2009-08-07
> **novafluxx said:**
> 

how much ram/memory does your mini 9 have?


512mb

---

### Post by ugm6hr on 2009-08-07
Do you mean that there is a "window trail" left behind when you move windows quickly?

Or is it something else?

Is video performance OK?

---

### Post by novafluxx on 2009-08-07
> **turbodellmini said:**
> 512mb

This is part of the issue. Less then 1GB of memory is going to slow any modern system down. I'm sure we can figure this out for you though!~~!

---

### Post by tgalati4 on 2009-08-07
Sounds like a regression:  Intel graphics performance should be good under Jaunty, but a change in Xorg version and the open Intel drivers undergoing a change can cause performance issues.

Wait for Koala or try Hardy.

---

### Post by novafluxx on 2009-08-07
> **tgalati4 said:**
> Sounds like a regression:  Intel graphics performance should be good under Jaunty, but a change in Xorg version and the open Intel drivers undergoing a change can cause performance issues.

Wait for Koala or try Hardy.

I second this assessment

---

### Post by turbodellmini on 2009-08-07
> **ugm6hr said:**
> Do you mean that there is a "window trail" left behind when you move windows quickly?

Or is it something else?

Is video performance OK?


Its not a trail, its more like a jagged rip.

[quote=novafluxx]Wait for Koala or try Hardy.[/quote]

Ok, trying Hardy now.  Will report back.

---

### Post by ugm6hr on 2009-08-07
Graphics performance is just fine on the Mini 9 with 945 chipset, apart from the window trails when moving windows quickly.

Multimedia etc plays OK.

I don't think this is a significant issue for most people; hence the lack of reports etc.  On the Mini 9, I think the majority of users maximise most windows during use in any case.

Your 512MB RAM may be contributing too (I have 1GB).

EDIT: Just seen your response above.  If it is truly a rip, then this must be your RAM available, since my (otherwise identical) hardware does not suffer this.  Consider using XFCE instead.  And remove netbook-launcher etc.

---

### Post by ddrichardson on 2009-08-07
I've an Aspire One, similar specs it runs Compiz fine with 512Mb. Adding two options to the device section of /etc/X11/xorg.conf helps:
```
Option "AccelMethod" "exa"
Option "MigrationHeuristic" "greedy"
```
The first of these messes up KDEs icons but UNR doesn't use KDE.

Also
```
export INTEL_BATCH=1
```In /home/$USER/.profile _might_ help.

---

### Post by ugm6hr on 2009-08-07
A similar xorg edit, apparently confirmed on this chipset (I have not tried):

See Bleeding Edge Method 2: [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

---

### Post by tgalati4 on 2009-08-07
There is also a switch to turn windows off when moving.  You just get a frame, when you drag a window, but no tearing.  Good for low-ram machines.

More RAM may help.  If Hardy works, then stick with that for a while.

---

### Post by turbodellmini on 2009-08-07
> **tgalati4 said:**
> There is also a switch to turn windows off when moving.  You just get a frame, when you drag a window, but no tearing.  Good for low-ram machines.


Do you know where I might enable this?

I tried hardy with the same result. I heard somewhere something about enabling syncing to vblank?  Does anyone know if this is the problem or is it unrelated?

---

### Post by turbodellmini on 2009-08-07
Okay.  So after a little reading I've come to the conclusion that it's either my picky vision or a lack of ram.

I think I'll order some ram on monday.  Thanks all for your help though, the ubuntu community seems awesome!:D

---

### Post by 3rdalbum on 2009-08-08
When using a 2D window manager, you will get an amount of tearing. The actual amount depends on the graphical power of your machine - for an Intel Atom-based netbook, that's not really a lot of graphical power, therefore there will be noticable tearing. Noticable for someone who's not used to it ;-)

The reason why there's tearing in Xorg and not in Windows is just due to architectural differences. X has some useful features, like the ability to run graphical programs from a remote machine on your local machine, that are said to cause the tearing.

Intel is in the process of rewriting their drivers and for the time being there is reduced performance on certain Intel graphics chipsets. If you can use Ubuntu 8.10 instead of 9.04 and 9.10, then you will get good performance and minimal tearing.

---

### Post by starcannon on 2009-08-08
> **turbodellmini said:**
> Thanks Paddy,

I'm currently running Ubuntu Netbook Remix 9.04 on a Dell Mini 9 with the Intel GMA945GME.

I'm running 8.04 on a dell mini 9, smooth as butter.

You can get the Dell Mini 9 Ubuntu 8.04 official *unofficial *restore iso here:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

Heres a direct link to the iso
[http://linux.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso](http://linux.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso)

GL and HF

---

### Post by dk06 on 2009-08-08
> **turbodellmini said:**
> Last night I got a wild hair and decided to dump windows xp on my dell mini in favor of ubuntu NBR.  The first thing I noticed was that when ever I move a window around it tears horribly.  Is this a normal expierence in Linux?  What can I do to get smooth movement like in Windows?  Is poor graphics performance like this a normal expierence?


Try easypeasy (Like UNR) & I've had good luck w/the Desktop 9.04 edition

---

