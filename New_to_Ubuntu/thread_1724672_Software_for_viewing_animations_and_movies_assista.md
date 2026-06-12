---
title: "Software for viewing animations and movies assistance"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by Tahinimoon on 2011-04-08
Hi Ubuntu has just been installed on my pc and I feel at quite a loose end having worked in XP. 

Can someone suggest what programm I can install from within Ubuntu that carries out the same function as Adobe Flash Player? 

I find that programs such as Facebook applications are incredibly slow to load and 'choppy' is the closest word i can find to describe my experience. My mouse is flickery. I don't know the 'technically' correct words to use. 

Does the term 'runtime application' refer to programs such as Adobe or is that something different? 

:(

---

### Post by rosencrantz on 2011-04-08
Don't worry, you'll learn to love it.
How to get flash on Ubuntu:
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)
Concerning the flickering - if you haven't installed a driver for your graphics card yet (which manufacturer), that could be it.
Go to  System->Administration->Additional Drivers (or Hardware Drivers on Ubuntu <= 10.04) and install what they recommend.
In what context did you get 'runtime application'? It can apply to a lot.
Cheers, rosencrantz

---

### Post by seawolf167 on 2011-04-08
Easiest way to get started with some of the proprietary formats is to install the restricted extras package. Open up a terminal (Applications -> Accessories -> Terminal) and type in the following

```
sudo apt-get install ubuntu-restricted-extras
```

then hit enter

---

### Post by Tahinimoon on 2011-04-09
Thanks Seawolf, I'm busy with installing the restricted extra's as you suggested. 

Thanks Rosenkrantz for your help as well. I will update my graphics card drivers as well. Regarding my 'runtime application' quiery - I was just enquiring whether Adobe Flash player is a 'runtime application' ? 

If I install Adobe Flash Player do I need to install anything else to make it run properly? Do i still need to install Adobe if I install the restricted extras? 

Can I play online Games on Ubuntu? My pc is partioned - so i have windows xp and ubuntu now. I wanted ubuntu as I have heard it is more efficient then xp. So I thought I'd try it out but i am concerned that I won't be able to play my games - I play mmorpg's and I have heard there are problems playing them with ubuntu. 

Hence me enquiring about the term 'runtime applications' - as I said I'm not tech savy with correct names so 'runtime' to me means 'effective running' of programs such as games, facebook applications etc. :confused:

I would prefer to just have one operating systems but if it means i keep xp for my gaming and ubuntu for my work I would keep it that way if it is difficult to resolve etc. So far I like ubuntu.

---

### Post by rosencrantz on 2011-04-09
The restricted extras package includes most of the non-free things you need for daily life, like codecs and flash, so you don't need to install anything else.
I suppose a runtime application is technically something running in a runtime evironment ([http://en.wikipedia.org/wiki/Runtime_environment](http://en.wikipedia.org/wiki/Runtime_environment)).
Whether you can run a game on Ubuntu depends on the game - if it's in-browser/flash like Facebook games, it can be played on any system.
For anything that needs to be installed:
Most popular games don't have linux binaries (too little demand). You might want to install the Windows emulator wine, the Windows versions of a number of games seem to run OK on it.
Search the Wine application database for the games you want to run ([http://appdb.winehq.org/](http://appdb.winehq.org/)).
Otherwise, you'll have to keep the double boot. You can run Windows apps in Windows running on a Virtual Machine (e.g. VirtualBox), but I wouldn't recommend that for graphically intensive games, it's usually rather slow.

---

