---
title: "connection drops every ~24 hours: Gusty 7.10, rt73 driver and NetworkManager"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2007-11-03
Hi everyone,

I did a fresh install of 7.10 a couple weeks ago and am having trouble with my wireless Internet connection.  Every once in a while (like once a day), I lose my connection (NetworkManager says that it's no longer connected and I can no longer load web pages).  The only way to get it to work again is to kill and restart NetworkManager, unplug my wireless device and plug it back in...then NetworkManager will automatically reconnect and everything is great for another day.  Importantly, I've noticed that the connection only crashes when I'm at the computer working online--it never goes down when it's just sitting idle--so there may be something that triggers it, but I've been observing it for two weeks and haven't noticed any pattern.

I'm not sure if the problem lies with NetworkManager or my wireless driver.  My wifi card is a D-Link DWL-G122 rev. C1.  Prior to 7.10, I used to have to compile the driver for it (rt73 from the serialmonkey project, [http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)) manually and use Rutilt instead of NetworkManager to connect, as NM didn't support WPA using that driver.  But since the 7.10 release, the card just works, using NetworkManager and WPA, out of the box, so I'm using whatever default drivers came with the 7.10 kernel.  Since I didn't have this problem before with my manually-compiled driver and have it now, I'm guessing that there could be a bug.

On the other hand, I think that it could be NetworkManager's fault because sometimes I have to kill -9 it because regular kill doesn't work, which makes me believe that something unstable might be going on with NM...of course, that instability could just be related to problems with the wifi driver and not be NM's fault.

I looked around and couldn't find anything similar to this documented online.  If anyone else is experiencing it, or has suggestions, I would appreciate them.  It's not a crippling problem, but it's annoying.

One last thought--I'm using a 64-bit kernel now; before, it was 32-bit...so that's another significant difference between when the rt73 card worked flawlessly and now, I guess, although as far as I know the rt drivers are completely stable under 64-bit.

---

### Post by kevdog on 2007-11-03
You are going to try a few different things here, since I cant explain exactly whats wrong in your situation. 

The problems with rt drivers and network manager are well documented.  The built ra/rt drivers in gusty are not proving to be that reliable.

My first step would be to recompile the drivers from serialmonkey and try to use those.  If this doesnt work then I would try using either a manual connection or rutilt.

Again most likely some experimentation will be necessary.

---

### Post by pytheas22 on 2007-11-03
Thanks for your help...I'll try these suggestions and see what happens.  I didn't want to recompile the drivers because now I'll have to do it every time I change the kernel, but I guess that's less annoying than having the connection break.

---

### Post by kevdog on 2007-11-03
Yes I know each kernel upgrade will require recompilation and installation of drivers, however once you do it about 2 - 3 times, you will be able to do this in less than a minute, so its really not a big deal.  I suspect one day these drivers will actually work out of the box, however if you are like me, I always like to run the newest drivers so I prefer to use cvs/svn sources.

---

