---
title: "Total newbie in need of assistance - please!"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by davidmchenry79 on 2011-03-02
Hi, everybody -

      I've been around Windoze computers for the last 15 years or so, and have finally made the switch to Ubuntu and love it so far - I wish I'd done this... oh, about 15 years ago lol. Here's my first question. I've been trying to install compizfusion, and keep getting to the part where the EULA for the truetype fonts pops up, and I can't get by it - it looks like I should click <OK> at the bottom, but it's not clickable and hitting Enter doesn't work either. When I eventually got fed up and exited the window, it said I was killing an active process and sure enough, compizfusion is nowhere to be found. Any ideas? By the way, I realize this might be a remarkably dumb question - but I'm totally stumped. Thanks for any help!!!

---

### Post by dnairb on 2011-03-02
IIRC pressing <TAB> will highlight <OK>. Then you can press <ENTER>

---

### Post by augustuen on 2011-03-02
Seems like the creators maybe have put it a lock that prevents you from continuing (I know blizzard does this). Have you tried scrolling all the way down?

---

### Post by josephmills on 2011-03-02
go to applications> accessories> terminal (or type ctrl+alt+t) and type in the following and copy and paste it ```
lspci
``` 
```
cat /proc/cpuinfo
``` ```
free -m 
``` what this will do is show us your cpu info(cat /proc/cpuinfo) your free ram in megabits (free -m)and your graphics card (lspci)

---

### Post by alegomaster on 2011-03-02
Maybe you have to preform a certain task before containing. Read what they say to do with the EULA.

---

### Post by dionysius on 2011-03-02
How did you install Compiz? It should be installed by default. The only thing you normally have to do is install ```
fusion-icon
``` or ```
simple-ccsm
``` (both enable you to make changes to settings and enable/disable effects, etc.)

---

### Post by davidmchenry79 on 2011-03-03
Thanks to all of you for replying - as it so happens, I found a workaround in a different post.  By updating and upgrading Ubuntu it installed the truetype fonts in a clickable context. After I clicked on them and finished the installation and rebooted, the compizfusion install went perfectly. Should I run into any problems in the future though, I'll be sure to refer to this post for some great ideas! Thanks again for taking the time to answer - I really appreciate it!! So far, I love Ubuntu!

---

