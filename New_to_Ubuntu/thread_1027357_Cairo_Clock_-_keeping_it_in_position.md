---
title: "Cairo Clock - keeping it in position"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by loobyloo on 2009-01-01
Hi
Following another thread here I've installed MacSlow's Cairo Clock [http://macslow.thepimp.net/?page_id=23#mark_7](http://macslow.thepimp.net/?page_id=23#mark_7)
which is a really attractive analogue desktop clock.

Two things:
1) has anyone worked out how to get it to stay where you want it to be?  Every time I reboot it starts in the top left; I want it in the bottom right.

2) Is there a way of removing the digital time from the date and time panel in the bottom right hand corner? I can see an option to remove the date but not the time. I suppose it's a reasonable assumption that most users will want it included by default but the analogue clock is sufficient for me.

Thanks
Cliff

---

### Post by Delever on 2009-01-01
I would suggest getting rid of MacSlow's Cairo Clock, and installing [screenlets]("apt:screenlets"):

```
sudo apt-get install screenlets
```

You can then load screenlets manager and add Clock, change it's theme to cairo-clock. It has many options and is well integrated into desktop.

---

### Post by loobyloo on 2009-01-01
Great, thanks for that.

Cliff

---

### Post by KPDXHAM on 2011-03-01
> **Delever said:**
> I would suggest getting rid of MacSlow's Cairo Clock, and installing [screenlets]("apt:screenlets"):

```
sudo apt-get install screenlets
```You can then load screenlets manager and add Clock, change it's theme to cairo-clock. It has many options and is well integrated into desktop.

YES! Thank you! 
I've been having to reconfigure the MacSlow's Cairo Clock every time I reboot since it was showing only a quarter of the clock and always on the top-left of desktop. I wanted it on top-right.
Now I installed the screenlets and have a clock that stays in place and at the correct size, etc. Oh .... yeah, it keeps good time also. ;) 

Also added Clear Weather Screenlet. Nice stuff! :)

(another Cliff)

---

