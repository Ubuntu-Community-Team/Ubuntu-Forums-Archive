---
title: "hp 5550 not printing"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by ametalguitarist on 2009-06-17
I'm a sub-novice when it comes to linux.  I'm having a problem with my printer not printing.
My system is:
Dell 2400 Dimension
1.5g ram
hp 5550 printer through printer port
Ubuntu 9.04 with pre-installed gnome x
Here is what I got for an error log. (see attachment)  I can't figure out what's wrong.  Please Help.

---

### Post by LewRockwell on 2009-06-17
[http://ubuntuforums.org/search.php?searchid=60683644](http://ubuntuforums.org/search.php?searchid=60683644)

---

### Post by ametalguitarist on 2009-06-17
none of those help.  I've tried searching before I posted.

---

### Post by LewRockwell on 2009-06-17
> **ametalguitarist said:**
> none of those help.  I've tried searching before I posted.

had to assume the safer option

---

### Post by LewRockwell on 2009-06-17
CUPS website and documentation:

[http://www.cups.org/](http://www.cups.org/)

[http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)

According to this information your HP5550 should work "perfect":

[http://www.openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_5550](http://www.openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_5550)

If I were you the first thing I would do is download 8.04 and see if it works

seems like 9.04 has had it's share of difficulties

---

### Post by ametalguitarist on 2009-06-17
I'm not sure how to build cups and install make and all that...I'm not that familiar with linux like I said.  The main thing is that the error message said it could not find the printer.  I changed the location of the printer and now it sends jobs without errors and says printing was complete but nothing was ever printed.

---

### Post by wpshooter on 2009-06-17
Is this a parallel port printer ?

How many drivers are you seeing listed in the printer setup section for this particular model printer ?  And have you tried ALL of the ones listed ?

---

### Post by ametalguitarist on 2009-06-17
Well it's working now.  Apparently the printer thought it had an empty ink cartridge even though it's a new one.  I put an old one in and now it thinks it's new.  So I guess it wasn't a driver or linux problem at all but my printer has alzheimers LOL 

Yes it's parallel port and there was only hp deskjet 5550 and pdf for my print options.  I do have cups installed and it says it cannot communicate but it printed anyway.  It still bugs me that I get errors saying it can't and then does anyway...I suspect an xsession problem??? who knows.

Anyway sorry to waste your time on this and thanks for the help.

---

