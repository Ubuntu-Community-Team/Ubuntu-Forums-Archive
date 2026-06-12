---
title: "nvidia 7600GT dock issue"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by adduds on 2011-01-19
Hello all!

I have a dual monitor system with a GeForce 7600GT

My problem is that cairo dock is split on both screens; half right side one left....

I've gone into dock configuration and position it on the screen right...but I want it on the bottom..

I think it has to do with xconf? I've heard of this....

---

### Post by adduds on 2011-01-19
I've tried muckin' around with nvidia-x-server-settings;

but to no avail...

I've set the position of each screen to right and left but it always defaults back to absolute... does this have something to do with it?

---

### Post by LowSky on 2011-01-19
Can you tell us what settings you using for Nvidia X sever settings?

Have you tried another dock, like Docky or AWN?

---

### Post by adduds on 2011-01-19
Screen one conf

[http://img413.imageshack.us/i/screen1bn.png](http://img413.imageshack.us/i/screen1bn.png)

Screen two conf

[http://img163.imageshack.us/i/screen2fx.png/](http://img163.imageshack.us/i/screen2fx.png/)

Also you can see what the dock is doing on my screen

ps. thanks for the quick response!!!

---

### Post by LowSky on 2011-01-19
try this first 

Basically, but right click the dock, and go to the config.
Go to the position tab and change the relative position all the way to the left to place the dock on the left display, and all the way to the right to place it on the right display. 


if that doesn't work try this
open a terminal
copy this command
```
gconftool-2 --type bool --set /apps/metacity/general/disable_workarounds false
```

reboot X

---

### Post by adduds on 2011-01-19
> **LowSky said:**
> try this first 

Basically, but right click the dock, and go to the config.
Go to the position tab and change the relative position all the way to the left to place the dock on the left display, and all the way to the right to place it on the right display. 


I've done the right hand dock and left hand....personally I want it on the bottom


> ```
gconftool-2 --type bool --set /apps/metacity/general/disable_workarounds false
```

is there an alternative code (reversal or undo) before I apply; just in case it messes up my GUI?

EDIT:

All that did was delete all my panels and everything on my primary screen (except cairo), and changed both screens backgrounds

pps.
How do I get my panels back now.....?

I tried this 
```
adam@adam-desktop:~$ gconftool --recursive-unset /apps/panel
adam@adam-desktop:~$ rm -rf ~/.gconf/apps/panel
adam@adam-desktop:~$ pkill gnome-panel

```

---

### Post by adduds on 2011-01-20
k i solved the gnome panels by apt-get remove --purge and reinstalling them

i still need to solve the cairo dock issue hit me up 

thanks!!! :) :p

ill give ya a :KS

'cmon :) :D

---

