---
title: "which linux better with ATI Mob Radeon HD 3470?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by mend on 2009-02-11
Does it make any difference if I choose lets say Kubuntu instead of Ubuntu, having an ATI Mobility Radeon HD 3470 graphic card?
I do have Ubuntu on my laptop already but I feel tempted to replace it with Kubuntu. Before I do that I'd just like to know if there's any Linux that works well with ATI? Is GNOME better than KDE for that?
Thanks :)

---

### Post by ibuclaw on 2009-02-11
What do you mean?

Gnome and KDE are frontends.

Ubuntu and Kubuntu use the exact same kernel and drivers to control hardware (or, to put in context with what you are asking, your graphics card) and sit ontop of the exact same XServer.

The only difference between them are the applications which carry out the same/similar job and the desktop environment.

If Ubuntu works brilliantly on your Laptop, Kubuntu will probably work just as well. But you may choose to either like or dislike the nature of the KDesktop.

Regards
Iain

---

### Post by mend on 2009-02-11
Thanks so far but Ubuntu is just one of many other Linux distribution..so would it make any difference if I chose some other Linux?

---

### Post by iBurger on 2009-03-04
As it is now, you cannot run ubuntu 8.10 with an ATI 3470. only 8.04 if you have this card, and want to use 3d graphics. (2d works though). The ATI driver is broken.

- things will probably change in the future.

---

### Post by ntrgc89 on 2009-03-06
Is there any word on whether 9.04 will see improved support for 3470? Or is it an issue on ATI's side?

---

### Post by shawndh on 2009-03-07
> **iBurger said:**
> As it is now, you cannot run ubuntu 8.10 with an ATI 3470. only 8.04 if you have this card, and want to use 3d graphics. (2d works though). The ATI driver is broken.

- things will probably change in the future.

That sucks! I was just about to post the same question because I have a 3470 card. Oh well, I'll have to load 8.04. Thanx for the info.

---

### Post by Ms_Angel_D on 2009-03-07
> **shawndh said:**
> That sucks! I was just about to post the same question because I have a 3470 card. Oh well, I'll have to load 8.04. Thanx for the info.

There is nothing wrong with 8.04 It's long term supported.

---

### Post by shawndh on 2009-03-07
> **MetalHellsAngel said:**
> There is nothing wrong with 8.04 It's long term supported.

Do you mind pointing me in the right direction for instructions on how to downgrade my 8.10 partition to 8.04?

---

### Post by Ms_Angel_D on 2009-03-07
> **shawndh said:**
> Do you mind pointing me in the right direction for instructions on how to downgrade my 8.10 partition to 8.04?

There is no way to downgrade, you'll just need to re-install, just make sure you back up all your goodies first.

---

### Post by nedyar on 2009-03-09
With new Catalyst 9.2 downloadable from ati web site only, you can use Ubuntu 8.10 with 3D acceleration.

---

### Post by freddymc on 2009-03-20
> **iBurger said:**
> As it is now, you cannot run ubuntu 8.10 with an ATI 3470. only 8.04 if you have this card, and want to use 3d graphics. (2d works though). The ATI driver is broken.


Hi! Is this still a problem? I've got the ATI mobility 3470 and drivers installed. 
What do you mean with "3d graphics"? 3d support in general or just special desktop effects?

I'm able to play 3d games like quake3 or nexuiz. But - I'm using Kubuntu 8.10 (KDE 4.2) - activating desktop effects makes things *very* slow: scrolling in firefox doesn't seem smooth, opening windows from the bar at the bottom doesn't work flawlessly and opening context menus (right click) shows (for less than 1sec) "graphic rubbish" (sorry, I don't know how to explain it in English) instead of the box with the context menu.

Disabling effects (Alt + Shift + F12) solves the problems and everything works fine (without eye candy, of course).

My System:
Thinkpad T400:
Intel Dualcore P8400 / 2,26 GHz,
2 GB Ram,
ATI Mobility Radeon HD 3470 / 256MB + 384MB shared (proprietary drivers and 3d installed)
This should be enough to activate the effects, shouldn't it?

Any hints?
Fred

---

### Post by ntrgc89 on 2009-03-20
I think he just means desktop effects, but I've never used Linux for anything 3D other than desktop effects so I'm not sure

I'm also on a T400, and the desktop effects don't work with the ATI card. They great with the integrated graphics tho, so I'd try running with that until better support comes out.

The post right before you mentioned some new drivers out, I might try those and if I do i'll report back.

---

### Post by iBurger on 2009-04-09
I'm a bit further on the learning curve now, then when i started with ubuntu two weeks ago :) 

**There are two drivers for ATI video cards.**
**1) fgrlx proprietary driver.**
- proprietary bin
- visual effects work
- works with 8.04, brokin in 8.10. expected to work again in 9.04 jaunty 
- see this wiki for information.

**2) community ATI driver**
- 2d just works.
- visual effects are not fully supported.
- (this is what you get if you install 8.10, with an ATI 3470)


There is a way to fix this. However, ATI users report that 3d acceleration with fgrlx is again fully supported in Ubuntu 9.10. Therefore, I'd suggest folks to skip 8.10.

>>>
[Unofficial ATI Drivers Wiki / Ubuntu Support.]("http://wiki.cchtml.com/index.php/Ubuntu")

---

