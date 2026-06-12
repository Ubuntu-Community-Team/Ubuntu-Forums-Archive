---
title: "Guitar Pro 6 installed on Karmic 64 bit"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Cinch64 on 2010-09-05
Thought this would be some help to others.
I found this info on installing Guitar Pro 6 (32 bit) on a 64 bit system. Works like a charm if you follow each step.


I've installed the 32bit deb on my Ubuntu 64bit machine. Here's the process I followed:

1. Open Terminal and enter the following commands:
  
wget [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb)

then enter:

sudo dpkg -i getlibs-all.deb

then enter:

getlibs /opt/GuitarPro6/GuitarPro

2. Once you've installed the above, then enter:

sudo dpkg -i --force-architecture guitarpro6.deb

(where 'guitarpro6.deb' represents the filename for the program - from memory, the current demo version filename of GP6 is GuitarPro6Demo-rev8217.deb)

Hope this info helps.


Guitar Pro 6 runs excellent on Karmic.

---

