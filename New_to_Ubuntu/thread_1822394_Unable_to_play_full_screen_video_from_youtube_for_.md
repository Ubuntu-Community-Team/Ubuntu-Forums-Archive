---
title: "Unable to play full screen video from youtube for example"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by Denis Hristov on 2011-08-10
Hello. I have unknown problem with that to play video on youtube. I mean all kind of video 240p to 720p....  My PC specifications:
CPU: AMD Athlon 3000+ 2GHz 512kb cache
RAM: 1,5 GB DDR
AGP: ATI Saphere Radeon 9550 256MB (with cooler)

So i think that configuration isnt low for Linux :/
I installed something... i guess video drivers via the terminal (actually i do the steps to prepare my ubuntu to play wow and everything is ok) but i get lagg when i play games.... the same lag for World of Warcraft and 4x4 Evo 2 ... for example. And if i play video on youtube and i press full screen button i see only frames... 3 - 5fps lol
I think something is going wrong, becouse i havent that problem on Windows XP, i havent it on Windows 7 too :/ help me please :confused:

---

### Post by CatKiller on 2011-08-10
Installing the Flash Aid extension will probably help you.

---

### Post by Denis Hristov on 2011-08-11
Well i get this one [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and yes the frames are running now, but is still here. The video sometimes is going to frames again and i can see artefacts and errors on the screen. And that extension works only for firefox. My problem with the basic windows games or any other videos is here :confused:

---

### Post by gandaran on 2011-08-11
> **Denis Hristov said:**
> Well i get this one [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and yes the frames are running now, but is still here. The video sometimes is going to frames again and i can see artefacts and errors on the screen. And that extension works only for firefox. My problem with the basic windows games or any other videos is here :confused:
the flash installed using firefox flash-aid addon works for every other browser too as it installs flash in the file system 
did you run the flash-aid wizard to select the best flash for you system?

---

### Post by CatKiller on 2011-08-11
That's not a great graphics card.

> **Denis Hristov said:**
> 
I installed something... i guess video drivers via the terminal (actually i do the steps to prepare my ubuntu to play wow and everything is ok)

It's really not clear what you mean here. Does System -> Administration -> Additional Drivers show that you're using the proprietary driver?

---

### Post by Denis Hristov on 2011-08-11
No... where is that wizard :/ i cant find it

Here's a picture about how it works my World of Warcraft
[http://imageshack.us/f/217/screenshotxma.png/](http://imageshack.us/f/217/screenshotxma.png/)
it runs the same way when i browse internet or do nothing.... 4x4 Evo 2 works at the same way too (thats a old game - 2004)

---

### Post by CatKiller on 2011-08-11
> **Denis Hristov said:**
> No... where is that wizard :/ i cant find it

Running ```
jockey-gtk
``` in a terminal should do the same thing.

---

### Post by Denis Hristov on 2011-08-11
"No propriety driver are in use on this system" thats the message... and empty list.
I'm really new on Ubuntu but i want to learn much of it :/ and i want it to replace my windows :)

---

### Post by CatKiller on 2011-08-11
It's possible that the proprietary driver doesn't support a graphics card that old. I don't have any experience with Ati graphics, I'm afraid.

[This page]("https://help.ubuntu.com/community/RadeonDriver") suggests that your card should be reasonably well supported with the open source driver, so it might be a case of undoing whatever it was that you did from the command line before.

---

### Post by Denis Hristov on 2011-08-15
My video card is supported as RV350   >>> (Radeon 9550)

RV350                       Radeon 9600PRO/9600SE/9600/9550, M10/M11, FireGL T2

---

### Post by Denis Hristov on 2011-09-26
wow... no answer :/

---

