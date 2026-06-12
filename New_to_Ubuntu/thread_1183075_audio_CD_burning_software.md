---
title: "audio CD burning software?"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by gfunkera on 2009-06-09
long story short, brasero doesnt work after jaunty upgrade.. it crashes exactly after a certain time period of being opened., regardless of the operation being performed at the time.
 
what other software can i use in place of brasero as my audio cd burning software?

---

### Post by skyjacker on 2009-06-09
> **gfunkera said:**
> long story short, brasero doesnt work after jaunty upgrade.. it crashes exactly after a certain time period of being opened., regardless of the operation being performed at the time.
 
what other software can i use in place of brasero as my audio cd burning software?
k3b is an excellant tool to burn cd/dvd's

---

### Post by oldos2er on 2009-06-09
Gnomebaker.

---

### Post by woedend on 2009-06-09
> **oldos2er said:**
> Gnomebaker.

I second gnomebaker as well.  I mean no offense to the brasero crew for their hardwork...but its buggy, unstable, and i've never really gotten it to do much for me.  I don't know why ubuntu ever made it default.
K3B is a bit more full featured...but KDE based.  And I dislike most things KDE, plus don't want the dependencies, so shy away.

---

### Post by andrew.46 on 2009-06-10
Hi gfunkera,

> **gfunkera said:**
> what other software can i use in place of brasero as my audio cd burning software?

Can I tell you that I spent a reasonable piece of my life creating a guide for copying audio cds from the commandline using cdrdao? cdrdao is the software that flashy guis like k3b use to create audio cds believe it or not. This guide has been pretty comprehensively underutilised on the Ubuntu Forums which has always saddened me more than a little :(.

So if you want to:

[LIST=1]
[*]Bring some happiness into my life
[*]Get flawless and error free audio cd duplication
[/LIST]

have a look at the guide:

Howto: Duplicate Audio CDs using cdrdao
[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

I have yet to produce a frisbee using this technique...

Andrew

---

### Post by nothingspecial on 2009-06-10
Another excellent guide Andrew. I use it. :D

---

### Post by MrWES on 2009-06-10
> **andrew.46 said:**
> Hi gfunkera,



Can I tell you that I spent a reasonable piece of my life creating a guide for copying audio cds from the commandline using cdrdao? cdrdao is the software that flashy guis like k3b use to create audio cds believe it or not. This guide has been pretty comprehensively underutilised on the Ubuntu Forums which has always saddened me more than a little :(.

So if you want to:

[LIST=1]
[*]Bring some happiness into my life
[*]Get flawless and error free audio cd duplication
[/LIST]

have a look at the guide:

Howto: Duplicate Audio CDs using cdrdao
[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

I have yet to produce a frisbee using this technique...

Andrew

+1 Andrew for cdrdao -- I've used that exact guide, and you can't get much easier than:

```
sudo cdrdao copy
```

Bill

---

### Post by andrew.46 on 2009-06-10
Hi,

Wooo hoooo! At least 2 users :-). gfunkera I hope that perhaps this guide will at least give you a glimpse of a possibility other than the sometimes troubled guis.

This guide has a big brother:

CD and DVD Writing from the Linux Command Line
[http://www.andrews-corner.org/burning.html](http://www.andrews-corner.org/burning.html)

which has never been expanded onto these forums as Ubuntu does not use Jörg Schilling's software but rather it uses the Debian fork.

Andrew

PS Apologies for moving a little off topic.....

---

### Post by MrWES on 2009-06-10
> **andrew.46 said:**
> Hi,

Wooo hoooo! At least 2 users :-). gfunkera I hope that perhaps this guide will at least give you a glimpse of a possibility other than the sometimes troubled guis.

This guide has a big brother:

CD and DVD Writing from the Linux Command Line
[http://www.andrews-corner.org/burning.html](http://www.andrews-corner.org/burning.html)

which has never been expanded onto these forums as Ubuntu does not use Jörg Schilling's software but rather it uses the Debian fork.

Andrew

PS Apologies for moving a little off topic.....

I've read that guide as I wanted to learn how to rip/burn DVD9 to DVD5 from the command line. I do pretty much the same, I use vobcopy -l; vamps to shrink it down to fit on a DVD5; dvdauthor; mkisofs and growisofs to get it all done. Very powerful and efficient command line tools!

That with ABCDE and there isn't much else I need :)

Bill

---

