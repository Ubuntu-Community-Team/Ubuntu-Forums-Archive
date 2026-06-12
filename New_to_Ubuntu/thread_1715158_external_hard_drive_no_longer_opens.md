---
title: "external hard drive no longer opens"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by ridisempre on 2011-03-26
Please Help! I have a Toshiba Stor.e art 2.5 external hard drive (with ALL my data on it) which was working fine about a month ago. Now all of a sudden when I plug it in, no icon appears on my desktop and if I try to open it from the Places menu, everything freezes. When I unplug it everything goes back to normal and it gives me this error: Could not find "/media/TOSHIBA EXT"... I really hope this doesn't mean I've lost everything... I had my hard drive die on me last month and I don't think I can go through this again...

---

### Post by hakermania on 2011-03-26
Firstly, before doing anything, try on another machine and back-up EVERYTHING if possible....

---

### Post by prshah on 2011-03-26
> **ridisempre said:**
> when I plug it in, no icon appears on my desktop and if I try to open it from the Places menu, everything freezes.

Please give some more diagnostic information as below: Note this will only give us more information, this is not a solution:

Open a terminal (Applications-Accessories-Terminal) and give the command```
 tail -f /var/log/messages
``` Now plug in your external drive, and wait a few seconds; try to open it as usual from the Places menu, then unplug as you usually do. 

There should be a bunch of diagnostic output in the terminal. Please copy/paste it here.

If you lose the terminal for any reason, you can also press alt+F2 and give the command```
gedit /var/log/messages
``` and paste back the last 50 or so lines from it.

This will give us more relevant information on how to approach the problem.

It can be:
a) A dying harddisk
b) Not enough power via the USB ports
c) Minor/major file system corruption

---

