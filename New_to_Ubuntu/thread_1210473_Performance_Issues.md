---
title: "Performance Issues"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Fhallax on 2009-07-11
Hey Ubuntu Forums. I've just recently made the switch from Windows to Linux and I am having a few problems with performance. Games are really slow. They look great but they are unplayable. My machine isn't exactly new, but it ran Fallout 3 on XP pretty well, but now if I try to play Nexuiz or even AssaultCube it fails miserably. Any suggestions? Is there some setup I need to complete? I'm at a loss.

Fhallax.

---

### Post by tacantara on 2009-07-11
Are you running those games through Wine, or are you running them on Windows in a virtual machine?  Or, is it neither, and these games are on-line?  You'll have to excuse me, as I'm not much of a gamer.

---

### Post by CLomax on 2009-07-11
Something might be chomping at your CPU cycles.

Run this in the terminal (**Applications** -> **Accessories** -> **Terminal**)

```
top
```

Take a look at the %CPU to see if there's anything using a lot of your CPU.

---

### Post by philinux on 2009-07-11
> **Fhallax said:**
> Hey Ubuntu Forums. I've just recently made the switch from Windows to Linux and I am having a few problems with performance. Games are really slow. They look great but they are unplayable. My machine isn't exactly new, but it ran Fallout 3 on XP pretty well, but now if I try to play Nexuiz or even AssaultCube it fails miserably. Any suggestions? Is there some setup I need to complete? I'm at a loss.

Fhallax.

Have you setup your graphics card. What make is it.

System>admin>hardware Drivers

---

### Post by Fhallax on 2009-07-11
Cheers folks. I hadn't set up my Graphics Card. I'm still a Linux n00b. Problem solved.

---

### Post by LewRockwell on 2009-07-11
it's great when a plan comes together

.

---

### Post by V17741N on 2009-07-12
I am experiencing a ton of lag on both the menu and in game using nexuiz and ubuntu 9.04 jaunty jackalope edition. anyway, every graphics thing is off as well as v sync. even went as far as to turn sound off. (sound doesnt lag by the way). I am running this on a stock HP Pavilion DV6000 only no web cam. you can find the specs here: [http://www.pcmech.com/article/hp-pavi...]("http://www.pcmech.com/article/hp-pavilion-dv6000-notebook-review/") and while it's an ok computer. it isnt running this game. Nexuiz did successfully run on windows but due to HP being stupid about getting me a restore disk, i switched to Linux. I'm using the current 242 release of nexuiz. i've tried both the SDL and the GLX, the game is awesome but i cant get it to work with Ubuntu 9.04 

Any help would be very appriciated. also, I'm going to load a yioutube vid of the issue so it could be better understood. and i'm sorry  if this is the wrong forum for this. i couldnt find a nexuiz forum.

---

### Post by V17741N on 2009-07-12
The video that I mentioned I'd be posting on youtube is: [http://www.youtube.com/watch?v=JKoNIixS7xo](http://www.youtube.com/watch?v=JKoNIixS7xo) Hopefully this gives you a better idea of what's going on.

---

