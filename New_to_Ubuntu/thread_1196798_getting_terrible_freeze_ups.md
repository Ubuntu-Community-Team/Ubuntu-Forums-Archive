---
title: "getting terrible freeze ups"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by DarinB on 2009-06-25
I have a core 2 duo with 4 gbs of ram. running 32 bit jaunty. 
I started watching the guild on line and i get really bad freeze ups i know it is related to firefox, i can't even click the mouse! so i have to restart, it's like using windows again!!! is there a way to force end using the keyboard because nothing works at all when that happens alreeady three times today. but it also happened while watching hulu the tonight show, (maybe conan sucked too bad, LOL) any ideas on how to ctrl alt del or something like that or why am i crashing on firefox 3.011?????????????????????? does a manual reboot mess things up like in windows????????? never had freezes before i started with feisty this is a new thing????

---

### Post by earthpigg on 2009-06-25
is your system up to date?

if so, have you tried opera? just to narrow down the cause of your lockups: [http://www.opera.com/](http://www.opera.com/)

---

### Post by philcamlin on 2009-06-25
run sudo apt-get update/upgrade 

see if that solves anything if not reinstall firefox

and go with something else like opera

---

### Post by prshah on 2009-06-25
> **DarinB said:**
> any ideas on how to ctrl alt del or something like that

[Magic SysRq keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key") 
In Summary:
Ctrl+Alt+(Shift, in some cases)+SysRq + R, E, I, S, U, B

However, it's better if you can solve your problem; maybe studying the log files (System-Administration-System Log) can give you a clue? (Hint: Look near the end!)

---

### Post by jmszr on 2009-06-25
DarinB,

This thread deals with the (9.04) ctrl+alt+backspace issue: [http://ubuntuforums.org/showthread.php?t=1134427](http://ubuntuforums.org/showthread.php?t=1134427) .

---

