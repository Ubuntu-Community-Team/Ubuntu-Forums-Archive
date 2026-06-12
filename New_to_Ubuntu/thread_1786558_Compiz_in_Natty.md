---
title: "Compiz in Natty"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by gfunkera on 2011-06-19
just installed Natty on an internet-less computer, i want wobbly windows and the cube! i downloaded the "Compiz Icon" and some other stuff through the software center (had do drag a desktop to internet ready area).. but when i got back home with the computer i couldnt find the menus and stuff for compiz so that i can mess with compiz.. i know its there cause i can do ps -e | grep compiz and it shows up with a PID and everything... 

how can i customize my computer to awesomeness like i was able to before??

---

### Post by GWBouge on 2011-06-19
You need the compiz-config-settings-manager, if that's not one of the things you've gotten already.  On occasion, while you're messing with settings in CCSM, you'll (or I'll, at least) get a slight glitch where the top panel and maybe window borders will turn some funky colors, but logging out and back in fixes it.

---

### Post by wildmanne39 on 2011-06-19
> **gfunkera said:**
> just installed Natty on an internet-less computer, i want wobbly windows and the cube! i downloaded the "Compiz Icon" and some other stuff through the software center (had do drag a desktop to internet ready area).. but when i got back home with the computer i couldnt find the menus and stuff for compiz so that i can mess with compiz.. i know its there cause i can do ps -e | grep compiz and it shows up with a PID and everything... 

how can i customize my computer to awesomeness like i was able to before??Hi, To get the cube working in natty use this link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed.
It sounds like you may have already messed up unity and compiz, I would reset unity and compiz before you install the cube, you can reset them by clicking on reset unity and compiz in my signature and follow the instructions, and I would reset both.

---

### Post by wildmanne39 on 2011-06-19
> **GWBouge said:**
> You need the compiz-config-settings-manager, if that's not one of the things you've gotten already.  Although do note, if you run the Unity interface:  Desktop Cube requires you to disable the Desktop Wall, which is required by Unity, so you'll have to login with the classic desktop mode.Hi, thats not the case anymore if he follows my instructions in my post it will work.

---

### Post by GWBouge on 2011-06-19
Ah, and I think I've even seen that resolution referred to somewhere else, too.  Sorry for any misinformation, I should think more before posting  XoD

Edited my post above.

---

### Post by gfunkera on 2011-06-20
im looking into your solutions and will respond when i am done trying them... just so you know, i couldnt get unity to work, the desktop loads up and then freezes, the only thing i can manipulate is the mouse cursor....

i just load into Ubuntu Classic and use Gnome... btw i managed to find some command, which i dont currently remember, that ran a check on my system for compatibility with unity and everything was 100% A-Okay, passed and ready to go...  but whenever i try running it, i have to hold my computers power button and power off the box cause it freezes (except for the mouse)!!!

i have a dual core system about 2ghz processor power
3 gigs ram
video card is ATI Radeon something something and it has like 170-something MB video memory.....

anyway, ill be back tomorrow or something with an update

thanks guys!

---

### Post by wildmanne39 on 2011-06-21
> **gfunkera said:**
> im looking into your solutions and will respond when i am done trying them... just so you know, i couldnt get unity to work, the desktop loads up and then freezes, the only thing i can manipulate is the mouse cursor....

i just load into Ubuntu Classic and use Gnome... btw i managed to find some command, which i dont currently remember, that ran a check on my system for compatibility with unity and everything was 100% A-Okay, passed and ready to go...  but whenever i try running it, i have to hold my computers power button and power off the box cause it freezes (except for the mouse)!!!

i have a dual core system about 2ghz processor power
3 gigs ram
video card is ATI Radeon something something and it has like 170-something MB video memory.....

anyway, ill be back tomorrow or something with an update

thanks guys!
Hi, my instructions for the cube are for people running unity, if you are using classic you can still install it that way but you should go to this link and do what it says afterward because you will not have good performance in classic because compiz needs to be downgraded when using classic.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.htm](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.htm)

---

### Post by Zombie_Z on 2011-07-12
> **GWBouge said:**
> You need the compiz-config-settings-manager, if that's not one of the things you've gotten already.  On occasion, while you're messing with settings in CCSM, you'll (or I'll, at least) get a slight glitch where the top panel and maybe window borders will turn some funky colors, but logging out and back in fixes it.

I have the issue of them not being there. and a log out doesn't happen to fix the issue. any suggestions??   Posted a response in a different thread, but this quote matches my issue, but not my solution??

---

### Post by Zombie_Z on 2011-07-12
!!!DISREGARD MY LAST POST, FOUND MY SOLUTION!!!     Thank god for genius' with signatures ;) u know who you are!!

---

### Post by hookitup on 2011-07-14
fast forward all the dumb stuff in this link you tube is a great source for visual learners
[http://www.youtube.com/watch?v=lVR1y9cJHWA](http://www.youtube.com/watch?v=lVR1y9cJHWA) , this will explain how to do cube without TERMINAL , and also if u want close and open effects like burn then you need to do this code after u have installed CCSM ```
sudo apt-get install compiz-fusion-plugins-extra
``` just play around with the settings, theres nothing u cant undo so go ahead and explore


oh and by install CCSM you can do wobbly windows , just make sure u fallow the steps in the video. i have done it on 5 pcs in my household and every one has had no issues at all,,
 and if you want some more i candy,  run this code and u will get like wigets type of things 
```
sudo apt-get install screenlets
```

---

