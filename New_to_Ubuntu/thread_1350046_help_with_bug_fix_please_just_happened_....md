---
title: "help with bug fix please just happened ..."
date: 2009-12-08
forum: New to Ubuntu
---

### Post by mrpervie on 2009-12-08
ok guys i will file a bug report if somone helps me fix this first...ok what i did....if you have a fresh install of ubuntu how there is a panel on top and on bottom....well what i did was i moved the top one to the bottom...so there were two at the bottom...so i  right clicked went to properties and then clicked auto hide on the upper panel.....ubuntu froze and i had to restart...now all i can see is one panel with nothing on it ...and i really do not know how to get around in terminal ...but it wont let me right click on the panel or anything to change setting add or remove etc....anyone done this before?...only reason i got on the net is i right clicked and made a launcher for firefox...luckly i had auto connect enabled

---

### Post by mikewhatever on 2009-12-08
Calm down, this isn't a bug. You can add stuff to the panel by right clicking on it.

---

### Post by mrpervie on 2009-12-08
nope its a bug...i no longer have the option to right click on the panel....they both ...like...merged...

---

### Post by mrpervie on 2009-12-08
actually...i found this...[http://ubuntuforums.org/showthread.php?p=8382959....guess](http://ubuntuforums.org/showthread.php?p=8382959....guess) ill give it a try....but if anyone has an easier way that would be great...arg!!

---

### Post by mikewhatever on 2009-12-08
Don't forget to file a bug report when finished.;)

---

### Post by mrpervie on 2009-12-08
eh i did this method ...forget all that rebooting nonsense....[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

ya know...a seasoned user such as yourself coulda just told me =P

---

### Post by kristine12 on 2009-12-09
You can do the following command at the terminal to restore your panel default configuration.


Shutdown the current running gconf editing daemon for the user
```
gconftool-2 --shutdown
```Delete your panel current configuration
```
rm -rf ~/.gconf/apps/panel
```Kill the panel process
```
pkill gnome-panel
```Logout then Login again...
That it.

Hope it helps....

Code Source: [ukripper]("http://ubuntuforums.org/member.php?u=229569")

---

