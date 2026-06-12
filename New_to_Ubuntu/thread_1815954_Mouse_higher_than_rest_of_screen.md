---
title: "Mouse higher than rest of screen"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by CaptainJamie on 2011-08-01
I've already posted this problem, but the solution last time isn't working. and technically the mouse is in the right place but the rest of the screen has dropped by 20 pixels. Anyway last time it was fixed by the graphics driver being installed but since updating to 11.04 it has happened again. When the screen resolution changes it fixes it though, so i wrote a little program that runs on start up
```
sleep 5
xrandr -s 800x600
sleep 2
xrandr -s 1024x768
exit
```but sometimes it doesn't run, that's why I put the sleep in, in case it ran too early. If there's a better solution I'd like to know. (this is my grandma's computer, which is why I can't just make a launcher and click it if it doesn't run.)

---

### Post by Jouke S on 2011-08-01
I've encountered the same issue a few times before too. 
To me it isn't worth the time trying to figure out what's causing it and fix it, as it only happened 2 or 3 times so far, and I know my drivers are fine. 
My 'fix' was restarting X (enable the ctrl-alt-backspace command to restart X) be sure to save unsaved data before you do it

---

