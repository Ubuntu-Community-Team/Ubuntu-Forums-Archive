---
title: "Problems with Visual Effects"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by VinoFuriaRoja on 2010-06-03
Hey guys/girls!

Im a newbie here to the forums and to Linux, but have been doing great with 10.04 since my install last week.  I had some problems with slowness when i first installed it doing a dual boot with windows, but i reinstalled it and did a full install on my laptop and erased windows completely.  Since then, it has been running like a champ!

My problem is this:  I had no problems with Visual Effects, being able to switch between the three modes, but then I started messing around with the theme effects, customizing it to look like a Mac desktop, installing AWN and Compiz.  Suddenly, when trying to change the theme back to the default theme and changing the Visual Effects, it would not let me....saying that Desktop Effects could not be enabled????  I didnt have this problem before I started messing around with the themes and customizing, so hopefully someone can help me out! 

By the way, I did search the forums and found nothing to my situation.  Thanks in advance!

---

### Post by VinoFuriaRoja on 2010-06-03
A little help from someone please?

---

### Post by elliotn on 2010-06-03
Type

compiz 

On ur terminal and post the output

---

### Post by VinoFuriaRoja on 2010-06-03
Here is what I get when I type "compiz" in the terminal:

mark@laptop:~$ compiz
compiz (core) - Error: Another composite manager is already running on screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Window manager warning: Log level 16: Another compositing manager is running on screen 0

---

### Post by VinoFuriaRoja on 2010-06-03
and not much exploring done...but this is part of the learning process right? :P

---

### Post by ssj6akshat on 2010-06-03
try compiz --replace

---

