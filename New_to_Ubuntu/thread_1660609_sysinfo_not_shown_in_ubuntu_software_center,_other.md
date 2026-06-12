---
title: "sysinfo not shown in ubuntu software center, other problems"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by al204 on 2011-01-05
hello ubuntu users...
I have the following problems...

1. I downloaded the sysinfo app some 90 min ago, it seemed to work ok until I tried clicking on the first icon on the left column (don[t remember what is was now)....this caused the app window to close automatically. this problem happened several times.

2. I thought removing and reinstalling the app would be enough to solve the issue. So I did....the problem now is that I cant find sysinfo in the ubuntu software center!! what is going on here?

3. I also tried using the terminal window, as suggested in a couple of webpages I found.....unfortunately...it did not work either.

what can I do? I want to use this app (sysinfo) to look into the various characteristics of my laptop.
I[m using ubuntu 11.04

thanks, regards

al.

---

### Post by TeoBigusGeekus on 2011-01-05
I don't know about the app you installed, but have you tried
```
lshw
```
from terminal to get info about your system?

EDIT: 11.04? That's still alpha man.

---

### Post by gordie69 on 2011-01-05
goto applications top left click acessories terminal type sudo apt-get install sysinfo

---

### Post by mc4man on 2011-01-05
In natty clicking on 'system' will crash the app, the other sections should work.
> 
cant find sysinfo in the ubuntu software center!
It's there, just search from 'get software' (provided by ubuntu) or in synaptic or apt-get

---

