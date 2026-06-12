---
title: "Ubuntu Hangs"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-06-15
I get this problem while playing games,while playing scroched 3d after every 4 to 5 min the full screen mode resizes itself to a small output mode and i have to double click it to maximise it again.
And while playing assualt cube after 4 to 5 min the same thing happens but here the keyboard and the mouse stops responding (but the games is working and i am dying as i cant mode) .So whats the problem 

I got the problem in 8.04 and in jaunty 
I tried playing assualt cube in minimized mode and it works without hanging

---

### Post by Sealbhach on 2009-06-15
Do you play games with Compiz effects enabled? Compiz can cause problems if you're running games. 

Me, I use the Compiz Fusion icon and I use it to change the Window Manager to Metacity before I start up a game, you get far less problems that way.

Hope this helps.

.

---

### Post by collinp on 2009-06-15
> **Sealbhach said:**
> Do you play games with Compiz effects enabled? Compiz can cause problems if you're running games.

For the OP, Compiz is "Advanced Desktop Effects Settings".

---

### Post by ravi_buz on 2009-06-15
> **Hellow said:**
> For the OP, Compiz is "Advanced Desktop Effects Settings".

So what should i do disable it every time i play a game or something else

---

### Post by stoogiebuncho on 2009-06-15
I've had the same problem, and found the culprit to be the screen saver.  Turning off the screensaver before playing the games seems to fix the problem.

To make it a bit less annoying I made little launchers for the games that have a small script that turns off the screensaver, launches the game, and turns the screensaver back on when the game closes.

Something like this:
```
#!/bin/bash
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 0
COMMAND TO START GAME OR PROGRAM
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 1
exit 0
```

Then you save that, make it executable, and update your launchers in your application menu to point to that script instead of the game.

---

### Post by Sealbhach on 2009-06-15
> **ravi_buz said:**
> So what should i do disable it every time i play a game or something else

Install the Compiz Fusion icon, this allows you to easily change the window manager from Compiz to Metacity. That's what I would recommends. Also, as suggested, switch off the screensaver.

.

---

### Post by ravi_buz on 2009-06-15
Thanks to both of u i will try them

---

