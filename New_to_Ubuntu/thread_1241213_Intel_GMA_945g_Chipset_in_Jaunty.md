---
title: "Intel GMA 945g Chipset in Jaunty"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by jacksterson on 2009-08-15
[tl;dr - I have an Dell Inspiron 640m laptop with integrated 945g graphics chipset and its very glitchy and slow]

I have an 8.1 installation cd, so after installing Ubuntu, I [naturally] updated to Jaunty Jackalope.

In 8.1, although the computer wasn't running as smoothly as I know it should (I've used Ubuntu in the past on the same computer, and it ran perfectly, afaik it was 8.1 as well), it ran smoother than it does now.

In Jaunty, I can't set my graphical settings any higher than [none], and every time I move and resize windows, its very glitchy.  Even my guifications from pidgin is glitchy in that after highlighting it with my cursor, it dissappears, but reappears after moving it....

Anyways, i've searched around, went through synaptic package manager, found that I had the correct drivers installed, and that there are quite a few people with this same problem, but with different computers.

I have a dell inspiron 640m laptop.

Can anyone help me :confused:

---

### Post by LewRockwell on 2009-08-15
maybe get more ram(didn't see where you noted how much you currently have installed)

maybe try out a 9.04 LiveCD to see if it's smoother for you(reason being, some have had success with "upgrades"...others have failed miserably)

the first thing we do when someone brings us an "internet version upgrade" is back everything up, clean off the partition, and install from a known good install disk(and yes that time is billed)

as always, your mileage may vary...

we now return you to your regularily scheduled programming...

.

---

### Post by jacksterson on 2009-08-15
Ram shouldn't be a problem, I have 2.5 ghz of ram.  

Plenty of space on my computer, so its not cluttered....  So should I just download jaunty jackalope and put it on a flash drive, then install again?

---

### Post by sasho_zl on 2009-08-15
The Intel drivers in Jaunty are messed up. You should downgrade or try alpha version of 9.10 where this has being fixed.

---

### Post by jacksterson on 2009-08-15
What about this? 
[http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)

Would this work on my laptop?

---

### Post by kukibird1 on 2009-08-15
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

or 

[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")


The first one solved my issues.

---

### Post by jacksterson on 2009-08-15
I've tried the first one, it didn't do anything to help :/

Actually, I've tried both, and neither helped :///

---

### Post by scorp123 on 2009-08-15
> **jacksterson said:**
> I have an Dell Inspiron 640m laptop with integrated 945g graphics chipset and its very glitchy and slow That's normal. :D

Intel's 945G is OK for _some_ compiz effects, but you should definitely keep it down. And no, you probably won't be able to run games on this thing. Ever. Intel's cards are simply waaaay too slow for this.

I myself use compiz all the time on my laptops (I e.g. find the "Exposé" effect highly useful). I can use the cube OK (but I can't use "transparent cube"), I can use effects such as "Expose", random animations, fire, zoom, transparency, but that's about it. But most of the fancier effects have to remain off.

And yes, I am using Ubuntu "Jaunty" 9.04

---

### Post by jacksterson on 2009-08-15
> **scorp123 said:**
> That's normal. :D

Intel's 945G is OK for _some_ compiz effects, but you should definitely keep it down. And no, you probably won't be able to run games on this thing. Ever. Intel's cards are simply waaaay too slow for this.

I myself use compiz all the time on my laptops (I e.g. find the "Exposé" effect highly useful). I can use the cube OK (but I can't use "transparent cube"), I can use effects such as "Expose", random animations, fire, zoom, transparency, but that's about it. But most of the fancier effects have to remain off.

And yes, I am using Ubuntu "Jaunty" 9.04

Oh no, of course not, I'm not even talking about compiz.  Just, everything is glitchy and slow, even with the graphics turned off completely.

---

### Post by sandyd on 2009-08-15
Have you tried the Intel graphics PPA?
i cant think of where it is off the top of my head, but google it.

---

### Post by scorp123 on 2009-08-16
> **jacksterson said:**
>  Just, everything is glitchy and slow, even with the graphics turned off completely. Oooh. :confused: That sucks of course. Hmmmm ... Is your laptop running at a slow speed maybe? I have seen this once on a laptop with a somewhat broken (=buggy) BIOS. The laptop could vary its speeds between 600 or so MHz up to 1.3 GHz. But for some stupid reasons it would keep running at 600 MHz, even if plugged in. And that of course brought its performance almost to a halt.

Maybe it's something like this? Can you check your CPU speed? There are various applets and what not that could show you the speed your laptop is running at. Normal behaviour would be that it runs at low speeds if idle but then speeds up the CPU if needed.

It might also be worth to check the BIOS settings. You usually reach that by pressing F2 or DEL or F10 when the laptop boots. It depends on the make of your BIOS, e.g. AWARD, PHOENIX, AMI ... they all use different key combos but usually it's one of those three keys I just mentioned.

I am aware that usually laptop BIOS'es won't allow you to change much, but it's still worth checking if there is a power-saving setting that might make the laptop creep so slowly. It's worth checking, just to be sure.

---

