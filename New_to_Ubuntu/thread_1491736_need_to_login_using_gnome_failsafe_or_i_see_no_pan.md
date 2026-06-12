---
title: "need to login using gnome failsafe or i see no panels"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by stinger30au on 2010-05-23
i have installed 10.04 on a pc thats many years old. it has an asus mainboard and a pentium 3 933 cpu and onboard video


if i start 10.04 with gnome fail safe everything works fine i can see the menu at top of screen that says


applications    places     system


but if i log out and set to login using gnome, i dont get the panels

however, my desktop loads and my mouse works and i can even press ctrl+alt+del and have a on screen option that says to shutdown or restart


any clues on whats going on and how to fix it??

thanks

---

### Post by stinger30au on 2010-05-24
with a bit of googling i found an answer

[http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/](http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/)

i will save it here for prosperity

In the terminal
 2. ***gconftool-2 — – shutdown (no space between the dashes  and no space between the dash and the word ‘shutdown’)***
 3. ***rm -rf ~/.gconf/apps/panel***
 4. ***pkill gnome-panel – ***That’s it!






the first time i did it and restarted i again had no panels for top/bottom


i had to save the session


do this by system
preferences
startup


and click in the box 


remember currently running applications


then shutdown and restart




presto!

---

### Post by jless on 2010-07-12
Thanks a lot stinger30au, I also had the same problem. It drove me crazy trying to solve it, I even re installed Ubuntu, to no avail! Here comes your solution, it worked wonderfully.

Thanks!!!:p

---

