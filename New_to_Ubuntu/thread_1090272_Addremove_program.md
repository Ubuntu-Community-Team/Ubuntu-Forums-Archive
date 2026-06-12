---
title: "Add/remove program"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by gogic on 2009-03-08
Hi,

I have installed a Ubuntu 8.10. I need eclipse so i used add/remove programs, found eclipse and installed it. But i got good old version 3.2 so am downloading new version now for manual install ( 3.4 ).

Problem is that i tried to uninstall old one first. Opened Add/remove programs, and tried to uncheck eclipse but i got error message that there are some dependencies and i need to use synaptic package manager to remove eclipse. So i said fine noone is perfect lets do it that way.

Opened manager searched for eclipse and marked all packages for complete removal. And managed removed them. I opened add/remove again and in programs there is eclipse again ! not removed and am getting same message as before when i try to remove it. 

It's not so big problem that i can't remove it but problem is that i can't reinstall it when repository gets a newer version !

So i have 2 questions :
1. How to remove it so i can reinstall it if i wont
2. Why there is no new version of eclipse in repository?

Sry if there is too much text am practising my English :)

---

### Post by konqueror7 on 2009-03-08
try doing in the terminal,
```
sudo apt-get autoremove --purge eclipse
```

as for your second question, some packages in the repos are maintained by individuals, so some of them maybe busy or just forgot about it. as for me, i usually try to use this before downloading from the repos so i can know the info,
```
apt-cache show <package>
```

---

### Post by gogic on 2009-03-08
Thx its fixed now. Probably there was a problem with multiple instances of add/remove app in different desktops.

Command worked ok, just hope that they will implement gui app info cos u dont know which app u are downloading.

---

