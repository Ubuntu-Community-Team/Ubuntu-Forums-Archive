---
title: "Vista -&gt; XP / Ub Dual Boot or VirtualBox?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Nico-dk on 2008-12-07
In a week's time I'll get a new Dell XPS M1530:
T8300 Core 2 Duo (2,40Ghz, 800Mhz)
4Gb DDR2 SDRam @ 667Mhz (2x2)
160Gb Free Fall Sensor HDD
256mb Geforce Go 8600M GT
Dell True mobile 355 Bluetooth
Intel pro 3945 wifi
9-Cell 85WHr li-on battery
Fingerprint scanner

This comes with Vista preinstalled, which I'll replace with a Ubuntu 8.04 LTS / XP dual boot setup (according to numerous posts here, Ubuntu 8.10 and m1530 don't seem to get along very well).

Potential problems after install:
> Touchpad will go awry
> Fan control / heat will not kick in as expected
> Media Direct Button. This is the only one I'm actually a little concerned about (thanks to Dell's hardcoded bloatware). It might be easily fixed though (found a [nice guide](http://forum.notebookreview.com/showthread.php?t=231747))

My plan is to update the bios
(would've wiped all partitions here, but apparently that's not a good idea when dealing with the Media Direct Button)
Install XP
Intall Ubuntu
Iron out any kinks

Alternatively someone more savvy in all things Linux, suggested I used VirtuaBox instead. Ay thoughts on that??

In any event, all this sounds nice and easy, but being a Linux newbie I'm sure I overlooked something, so please help a newcomer out, by pointing out the holes in his plan.
Thanks for your time :)

---

### Post by Nico-dk on 2008-12-08
So I got all my bases covered?
... and there's no difference between dual booting and VirtualBox?
(I know there's a differences, I'm just bumping my own topic here ;) )

---

### Post by howefield on 2008-12-08
One difference between dual booting and using virtualbox is that a guest system running on virtualbox does not have direct access to the hardware, but uses virtual drivers supplied by the VM. So windows inside a virtualbox wouldn't be much good for gaming.

Dual booting means both systems have direct access to the hardware. 

One other consideration is that you need a reasonable amount of memory, to run both simultaneously, but you have that covered with 4 gig.

---

### Post by binbash on 2008-12-08
If you are planning to play games, then you will do dual boot instead of virtualbox

---

### Post by slinkey1981 on 2008-12-08
No offense to Sun, but if it were me, I would dual boot. My pc isn't exactly the best and I like squeezing every once I can from it's aging hardware.

I'm sure there are people who will disagree with me, but sometimes you just have to go with what will work the best for you.

It all comes down to your freedom of choice, and if you think VirtualBox meets your needs better than dual booting.

Just my 2 cents.

---

### Post by weezerisrock on 2008-12-08
Depends on how much you want to iron out the kinks as well.  XP will not work in ubuntu til you have loaded virtualbox or some other VM system and then install XP.  Seeing some of the potential problems you have listed as well as what you said about ubuntu not running well on that particular machine you may be more interested in Dual booting so you have something workable while you iron out your kinks.

P.S. I dunno how Dell does things but a lot of personal machines thru HP have ZERO xp support  (meaning they don't offer drivers) and kind of force you to use Vista.  Unless the machine says "Backwards compatible with XP"  I would be wary.

---

### Post by residualbit on 2008-12-08
What do you need XP for anyway?

With that hardware you should be able to run most apps just fine with Wine.

---

### Post by dragos_iliescu_2005 on 2008-12-08
My opinion, dual boot is the best. In this way you will have all the system capability work for you for both win and Linux too. Depending on what you decide to work with under Linux, Wine or VirtualBox can be used as for limited capabilities.

---

### Post by Nico-dk on 2008-12-08
Thanks everyone :)
I'll definitely go DB.

XP will be used strictly for gaming. It seems Linux is a lot of good things, but a gaming OS it's not (despite a few Linux consoles being released)

**weezerisrock:**(yes it is)
I don't worry about the support, I've been slipstreaming XP cds for years, so drivers shouldn't be a problem.

> **binbash said:**
> If you are planning to play games, then you will do dual boot instead of virtualbox
I do, so thanks

---

