---
title: "Ubuntu 10.04 refuses to shut down"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by nandan on 2010-09-26
Have a newly upgraded computer and have installed 10.04 on it, along with win xp.
Intel i3, 2GB RAM

Ubuntu is blazing fast and am enjoying it. Have one problem: It does not shut down. It hibernates, but when I click on shut down, it asks me if I want to shut down. On clicking "Shut down"...nothing happens. 

If I try to do this via ctrl alt delete, it is a similar story. I see the pop up called "Shut down the computer" with options of shut down, restart etc. and when I choose shut down...again, nothing happens!
Could somebody pls help?

---

### Post by adit on 2010-09-26
What happens when you type into terminal
```
sudo shutdown -h now
```

---

### Post by nandan on 2010-09-26
@ Adit:
The command allows me to shut down the system. 
Some observations: 
The problem seems to occur when the computer has gone in screensaver mode and then resumed.
also, I read on another thread that closing Open Office quickstarter solves the problem. I tried that and it worked. 
However, would be great if there is a better solution. :)

---

### Post by nandan on 2010-09-28
OK, Solved it by looking at solutions in other threads. 

Basically removed those buttons form the panel and then put in the shutdown button (right click on panel->Customize).

---

