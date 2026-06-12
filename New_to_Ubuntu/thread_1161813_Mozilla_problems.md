---
title: "Mozilla problems?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by scream_sayonara on 2009-05-17
Hi.. i think there might be something wrong with my browser. 

I've never been able to watch youtube videos, the browser just goes grey and i have to quit it. This was kind of annoying, but i got used to it and just avoided youtube.

Now however I can't use myspace either, it just simply wont load the pages.. I know this isnt a problem with myspace because its fine for everyone else...but every other page i go to works fine.

Also sometimes when i load pages with drop down menus such as babelfish, the browser will just close itself and disappear.

Could these problems all be related? I have looked into the flash thing, and im pretty sure i have the appropriate adobe plugin from the adobe website, but further than that, i'm stumped.

Any ideas?

---

### Post by bruno9779 on 2009-05-17
I had many troubles with adobe's plugin.

I cannot remember what replacement i installed to get Flash running smoothly, but that is the direction you should be looking at

---

### Post by diablo75 on 2009-05-17
> **scream_sayonara said:**
> 
Any ideas?

What version of Ubuntu are you running?

---

### Post by bumanie on 2009-05-17
I followed [this]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html") to get flash working on 9.04, 64bit

---

### Post by scream_sayonara on 2009-05-17
im running intrepid 32bit

---

### Post by podginater on 2009-05-17
> **bruno9779 said:**
> I had many troubles with adobe's plugin.

I cannot remember what replacement i installed to get Flash running smoothly, but that is the direction you should be looking at

I couldn't get adobe to install in firefox for some reason so i ended uo having to install shockwave which runs videos from youtube just about with occasional crashes but somethings will just not play like chris pirillo's live stream for example which is a bummer.

Anyone have any ideas on how to run adobe's plugin on Firefox 3.0.10 on Ubuntu 9.04 ( i never had the problem in 8.10).

---

### Post by scream_sayonara on 2009-05-26
Ok so now i think the myspace has nothing to do with the flash..


but... can someone please walk me through how to check i have the right flash plugins for my browser?

i have tried getting a couple of things through synaptic, including a plugin that turns flash things to buttons, and also downloading debs from the adobe website and stuff..

but i still cant watch youtube videos... im sure its a really easy thing to fix if you have any idea what youre doing...

thanks &#10084;

---

### Post by gandaran on 2009-05-26
> **scream_sayonara said:**
> Ok so now i think the myspace has nothing to do with the flash..


but... can someone please walk me through how to check i have the right flash plugins for my browser?

i have tried getting a couple of things through synaptic, including a plugin that turns flash things to buttons, and also downloading debs from the adobe website and stuff..

but i still cant watch youtube videos... im sure its a really easy thing to fix if you have any idea what youre doing...

thanks &#10084;
the only adobe flash package you should have installed is flashplugin-nonfree, this package is part of ubuntu-restricted-extras meta package so just unsure ubuntu-restricted-extras is installed, thats all you need for flash and video codecs.
for this flash plugin to work properly you must remove any other flash packages installed, packages to remove
adobe-flashplugin
swfdec-mozilla plugin 
mozilla-plugin-gnash
any adobe flash plugin installed manually
also update synaptic before installing the restricted packages, either click the reload button or run *sudo apt-get update*

---

