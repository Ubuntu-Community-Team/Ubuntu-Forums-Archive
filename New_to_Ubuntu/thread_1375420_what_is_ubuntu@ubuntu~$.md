---
title: "what is ubuntu@ubuntu:~$"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by jimsbluegras7 on 2010-01-07
I am extremely new. I had a problem with my monitor going to Low Resolution. I read some articles on how to fix it and when I tried one things really got bad. It could not boot. Finally, I tried to put in the Ubuntu disk and just wipe and reload the whole program but it would not do that either. 
 
The final result when the screen stops is I have a line that says [EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] .
 
Is there a way I can format the hard drive and reload the whole program?
 
I don't know what to do with it. I am working form my Windows computer right now. I was trying to switch to Linux on an old computer and eventually try to switch completely over.

---

### Post by warfacegod on 2010-01-07
ubuntu@ubuntu:$ is command prompt for a Live session. Using ubuntu without in stalling it. It looks like ubuntu is trying to load Live but gives you that because of a video card issue. I would take the disc or usb drive out, shut off the computer (unplug for 30 seconds), and start all over.

---

### Post by kansasnoob on 2010-01-07
**[COLOR="Red"]Only if you want to wipe the drive![/COLOR]**

If you're trying to install to the whole disc, that is wipe everything on that machine, boot the Live CD choosing "Try without changes ..." and go to System > Administration > Gparted (aka: partition editor).

Delete everything and try again.

---

### Post by theozzlives on 2010-01-07
Sounds like you're having video issues with the live CD. I'd try the alternate (text based) CD to do your install.

---

### Post by ndefontenay on 2010-01-07
Hi.

If you have video card issues, try to see what it is said about it on the internet first.

Give a bit more information about your video card already.

DON'T delete everything to try again. It's a major risk you will be taking. What if you're left with just a command line to work from. It's fine for advanced users but not beginners.

When you know where you're stepping with that video card of yours then you can take actions. Such as trying to install it using the text mode instead (did anybody else manage to get to the GUI after installing in text mode? I would like to know if I were you)

Nico

---

### Post by theozzlives on 2010-01-07
> **ndefontenay said:**
> Hi.

If you have video card issues, try to see what it is said about it on the internet first.

Give a bit more information about your video card already.

DON'T delete everything to try again. It's a major risk you will be taking. What if you're left with just a command line to work from. It's fine for advanced users but not beginners.

When you know where you're stepping with that video card of yours then you can take actions. Such as trying to install it using the text mode instead (did anybody else manage to get to the GUI after installing in text mode? I would like to know if I were you)

Nico

I installed Karmic on a system with a MSI MB with a nVIDIA 6 series with alternate and rebooted into GUI, downloaded the drivers from nVIDIA and everything worked out fine.

---

