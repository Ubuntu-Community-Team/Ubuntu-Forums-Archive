---
title: "xorg.conf help"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by rodneymullen on 2010-01-16
hi

Is my xorg.conf supposed to be empty? I'm using 9.10 and when i open the file none of the information is filled in. Am I supposed to manually edit in the info? Where do i find the imformation? 



thanks


Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by warfacegod on 2010-01-16
I think it depends on if you've change your monitor settings or not, resolution, refresh rate, etc. but don't quote me on that.

---

### Post by falconindy on 2010-01-16
Upstream is attempting to phase out the need for xorg.conf. To that effect, recent releases of xserver aren't being shipped with a default xorg.conf, but you still might find that you need to create and add to one. 'man xorg.conf' has some good info. That particular manpage might not be available on Ubuntu though, so here's a web link...

[http://www.x.org/releases/X11R7.5/doc/man/man5/xorg.conf.5.html](http://www.x.org/releases/X11R7.5/doc/man/man5/xorg.conf.5.html)

---

### Post by bodhi.zazen on 2010-01-17
> **rodneymullen said:**
> hi

Is my xorg.conf supposed to be empty? I'm using 9.10 and when i open the file none of the information is filled in.

Yes, xorg.conf is now "depreciated". Nvidia cards still use it however ;)

> Am I supposed to manually edit in the info? Where do i find the imformation?

What are you trying to do and what how to are you following. Perform a google search on your hardware (video card and monitor). Unless you describe your problem, hard to give a solution.

---

### Post by abhiroopb on 2010-01-17
From what it sounds like you don't actually seem to be having any problem (correct me if I'm wrong please). Unless you are having a problem there isn't any need to touch xorg.conf.

---

### Post by rodneymullen on 2010-01-17
I'm trying to play Starcraft on wine. There are fixes to the lag I'm experiencing but they involve editing the xorg.conf. It just seemed like everyone else's xorg had all the information beforehand. Anyway, is it safe to just find the information myself add it in?


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149)
[http://www.teamliquid.net/forum/viewmessage.php?topic_id=61452](http://www.teamliquid.net/forum/viewmessage.php?topic_id=61452)

maybe cause im on 9.10?

---

### Post by warfacegod on 2010-01-17
> **abhiroopb said:**
> From what it sounds like you don't actually seem to be having any problem (correct me if I'm wrong please). Unless you are having a problem there isn't any need to touch xorg.conf.

Often times using a GUI to set up, for instance, a second monitor doesn't work forcing the user to resort to modifying the xorg.conf file.

---

### Post by warfacegod on 2010-01-17
> **rodneymullen said:**
> I'm trying to play Starcraft on wine. There are fixes to the lag I'm experiencing but they involve editing the xorg.conf. It just seemed like everyone else's xorg had all the information beforehand. Anyway, is it safe to just find the information myself add it in?


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149)
[http://www.teamliquid.net/forum/viewmessage.php?topic_id=61452](http://www.teamliquid.net/forum/viewmessage.php?topic_id=61452)

maybe cause im on 9.10?

It should be. If you have any issues, simply deleting your xorg.conf file contents (not the file itself) should revert you back to where you started.

---

