---
title: "Drivers for USB antenna will not install."
date: 2005-09-10
forum: Networking &amp; Wireless
---

### Post by Frinkahedron on 2005-09-10
I have a netgear MA101 usb antenna, which I read could be configured for linux.

I get ndiswrapper installed and all that good stuff...

Then I go to install the drivers of the CD, do the ndiswrapper -i (I forget the exact file name).inf

ndiswrapper -l then lists:

driver: Invalid Driver!


I've tried all the inf files on the CD, none work.

---

### Post by mlomker on 2005-09-10
I did some searches and it doesn't sound very promising.  I'd recommend getting a different card that has native linux support.

I found [this web site](http://atmelwlandriver.sourceforge.net/news.html) that offers a native linux driver but it requires recompiling the kernel...not something that someone new to linux would want to pursue.

---

