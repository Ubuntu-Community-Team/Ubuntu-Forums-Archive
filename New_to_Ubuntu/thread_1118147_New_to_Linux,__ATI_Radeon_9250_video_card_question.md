---
title: "New to Linux,  ATI Radeon 9250 video card question"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by 0Hz on 2009-04-06
Ok, so I'm just starting out with Linux (Ubuntu 8.10).  The system I'm running it on has an ATI Radeon 9250 which I normally use to drive dual monitors in Windows.  The monitors are an HP w1707 (native 1440 x 900) and a much crappier Sony secondary monitor that I run at 1024 x 768. 

Right now the best I can manage in Ubuntu is 1024 x 768 on the HP monitor (with no secondary display).  I'm not really all that concerned with using the secondary display, I just want to know if there is a way to set the main monitor to a higher resolution (like 1440 x 900).

I know that there are ATI Proprietary drivers available, but again, I'm a total Noob with Linux, so should I try the ATI drivers?

Is it difficult to set up the proprietary drivers?

Any advice is greatly appreciated.

---

### Post by $elvis$ on 2009-04-07
Mate I have the same graphics card and all I can tell you is go and buy a new one...Today I'm getting myself a new one... Gonna burn this one with a torch... :D

OR:
You can try to build your own drivers:
```
https://help.ubuntu.com/community/Radeon_9200/9250_(RV280)_and_DVI
```
I didnt had any luck with that method...
Good luck anyway...
Cheers....

---

### Post by Therion on 2009-04-07
> **0Hz said:**
> I know that there are ATI Proprietary drivers available, but again, I'm a total Noob with Linux, so should I try the ATI drivers?
Absolutely!

To install them simply go to System/Administration/Hardware Drivers and look for a "Restricted Driver".  Double-click to install it.  That *should* be all there is to it.  If you DON'T see a restricted driver available, post back and we can install the ATI Restricted Driver manually.  You're *certainly* not going to get the most out of your card without the restricted driver in charge of things.

---

### Post by Cybie257 on 2009-04-07
> **0Hz said:**
> Ok, so I'm just starting out with Linux (Ubuntu 8.10).  The system I'm running it on has an ATI Radeon 9250 which I normally use to drive dual monitors in Windows.  The monitors are an HP w1707 (native 1440 x 900) and a much crappier Sony secondary monitor that I run at 1024 x 768. 

Right now the best I can manage in Ubuntu is 1024 x 768 on the HP monitor (with no secondary display).  I'm not really all that concerned with using the secondary display, I just want to know if there is a way to set the main monitor to a higher resolution (like 1440 x 900).

I know that there are ATI Proprietary drivers available, but again, I'm a total Noob with Linux, so should I try the ATI drivers?

Is it difficult to set up the proprietary drivers?

Any advice is greatly appreciated.


If you have a 64-bit capable CPU, I would recommend trying Jaunty Beta 64-bit. Why? I have not had any better experience with my ATI video card with any other version of Linux/ATI Drivers til now. Since it's 64-bit, there doesn't seem to be any proprietary drivers (don't quote me, just not seeing them or looking for them yet). 

I am not only able to easily change resolutions per screen like never before, but I can also turn of one screen on-the-fly (via display settings), with no need to restart X (GUI Desktop) or reboot. It just works. 

I'm not sure about the 32-bit Jaunty as I went right to 64-bit and glad I did. There are so many improvements that I am noticing, that I will never go back to any version prior. :) 

Since you are just starting out, you most likely don't have a lot of custom programs installed or data on your system. I seriously recommend you try it. At least try the LiveCD version and see how it works. 

-Cybie

---

### Post by 0Hz on 2009-04-26
This thread is a little old now, but I thought I'd provide some follow-up information for the benefit of others with similar old-ish hardware.  Thanks to those who provided advice, without it I would have been completely lost.

Unfortunately, after messing about and breaking/ reinstalling my system several times, I did not come up with a solution to getting better performance out of my video card.  (Probably on account of me being a ham-fisted noob.)

However, having just eagerly installed a fresh copy of 9.04, I am happy to say that I have my video card pushing full native resolution (1440 x 900) to my main monitor. (I have not tried dual-screen large desktop settings yet.)

I cannot overstate the ease of getting my display settings right in Jackalope.  My hat is off to the developers.

Here is a general description of my system:

Heavily modified HP Pavilion 734n

AMD Athlon XP 2400+
2GB DDR RAM (I can't remember the speed)
SoundBlaster Live! Value
ATI Radeon 9250
HP w1707 Monitor

---

### Post by gorg0th on 2009-08-14
0Hz,

Did you ever manage to see the dual screen working perfectly with this card?

---

