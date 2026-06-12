---
title: "visual effects are disabled"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by siddardha on 2011-02-06
Hello everyone

I am a linux novice and i just installed ubuntu on my Lenovo Ideapad Z560.Everything went well,I updated the software and installed additional drivers for wireless card and nvidia graphics card.So i started tinkering around and i found that i could not change the level of visual effects.I get the window like this

[IMG]http://img809.imageshack.us/img809/7472/screenshot1zcw.png[/IMG]
[IMG]http://img203.imageshack.us/i/screenshotit.png/[/IMG]

please help :)

---

### Post by Daveth on 2011-02-06
Hallo. Welcome to the Ubuntu Forums.
Have you tried re-loading the graphics driver since it stopped working? Might be worth looking at System/Admin/Hardware drivers, running that, and seeing if they need re-loading or "reminding" that they are there. 
Get back if you are still stuck.

---

### Post by hansolo4949 on 2011-02-06
Go into the software center and see if you have fusion, compiz, or compiz fusion installed (I cannot remember the exact name). If you dont have it installed, installl it, because that's what you need for the special effects. It comes with Ubuntu, so maybe you uninstalled it while you were doing something?

---

### Post by Hedgehog1 on 2011-02-06
You will find compiz itself is loaded using the 'Synaptic Package Manager'.  It may still be loaded, but checking like *hansolo4949* says should be done.

Once loaded (or you have verified it is still loaded), you may need to load the 'Compiz Config Settings Manager' using the software center to get a GUI to set your level of animations in great detail.

I found that after un-installing and re-installing copmiz for my Nvidia card to 'show off', I too was greyed out of the same screen, but had MUCH more fun setting all the cool animation details in the ccsm GUI.

I love those 'Wobbly Windows'. They just make me smile...

:KS

---

### Post by siddardha on 2011-02-07
yessssss i managed to get it by installing compiz from the software center 
hmmm you are saying that it comes default...i didn't remove it

---

### Post by sffvba[e0rt on 2011-02-07
> **siddardha said:**
> yessssss i managed to get it by installing compiz from the software center 
hmmm you are saying that it comes default...i didn't remove it

Also well that ends well I guess... may have been something to do with your graphics set-up at initial install, but hey, seeing as it is working enjoy it :)


404

---

### Post by siddardha on 2011-02-07
> **siddardha said:**
> yessssss i managed to get it by installing compiz from the software center 
hmmm you are saying that it comes default...i didn't remove it

okay another problem came up.....When i selected the visual effects from none to extra or normal the screen flickers and a dailogue box appears aking whether i want to keep these settings and i clicked on keep settings.

But nothing changed so when i returned to visual effects again option none is selected i repeated the process but it returns to none again 

P.s I have the graphics driver installed

---

### Post by siddardha on 2011-02-07
Bump
 any help?

---

### Post by siddardha on 2011-02-07
bump....some help please

---

### Post by Elfy on 2011-02-07
People will come along when they can - please do not bump threads more than once in 24hours

---

### Post by realzippy on 2011-02-07
As formerly suggested in this thread,do not touch the visual effects
settings by right-click desktop.For some reason (bug?) compiz gets messed up when doing this,
Configure the desktop effects (compiz) with ccsm as suggested and do not touch the "right-click on desktop/visual effects" settings afterwards,they will be unchecked
although compiz runs..(screenshot).

---

