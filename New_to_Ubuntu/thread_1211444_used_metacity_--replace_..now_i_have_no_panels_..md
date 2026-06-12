---
title: "used metacity --replace ..now i have no panels ."
date: 2009-07-12
forum: New to Ubuntu
---

### Post by djmh on 2009-07-12
well, i hit alt + f2 and i ran metacity --replace ...and now i have no panels.
or the exit minimize and maximize for my browser.

if i open terminal and run "metacity"
it gives me back my browsers exit minimize and maximize.
but i cant close terminal or i will lose them again.

so does anyone know how to get my panels back ?
and my exit maximize and minimize without having to run terminal ?

by teh way, i can not run alt + f2 again ... it just wont appear ...
i tried running some commands to reset my panels, but none of them worked.

any help would be great !!

---

### Post by raymondh on 2009-07-12
what happens when you press F11?

---

### Post by djmh on 2009-07-12
it will make my browser go full screen.

---

### Post by earthpigg on 2009-07-12
try (ctrl + alt + backspace)

should restart X... if we're lucky, it will restart X with all the panels and whatnot back.

(i know the new way is supposed to be right alt + print screen + k.... the dell mini 9, which he has, does not have a right alt key, and left alt does not work)


if you can somehow get to an alt+f2 window, 

> gnome-appearance-properties %F

will open the system -> preferences -> appearance menu.

---

### Post by djmh on 2009-07-12
hey man, thanks for the help ... but no worries, im just going to start over ... i want to give gos a shot ...and then i might stick with it or just go with a straight up unr downlaod.
peace all...

---

### Post by raymondh on 2009-07-12
> **djmh said:**
> hey man, thanks for the help ... but no worries, im just going to start over ... i want to give gos a shot ...and then i might stick with it or just go with a straight up unr downlaod.
peace all...

Very well.  I also use gOS which is a derivative/based off 8.04 Hardy.

For future reference, maybe...

In 8.04 Ubuntu, I lost my panels once and used this link.  Note it involves a rm/rf command so you may want to consider/research.

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Another option is to remove and re-install ubuntu-desktop

sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop

Good luck with gOS.  I like it myself and/but have found most of the fixes here at UF.

---

