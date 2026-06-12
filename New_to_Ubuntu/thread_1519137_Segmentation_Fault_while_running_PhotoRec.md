---
title: "Segmentation Fault while running PhotoRec"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by Lyos on 2010-06-27
I had accidentally reformatted and installed ubuntu on this external (chose the wrong drive during setup X/) and am trying to get some of the files back that haven’t been overwritten. I got a segmentation fault error after about an hour and a half of scanning my 300GB external.  Some of the files have been recovered up until the segfault. Any ideas as to why this may be happening and were I whould go from here?

Here's the terminal screen during the error:
[http://www.prism.gatech.edu/~cscholes3/segfault.png](http://www.prism.gatech.edu/~cscholes3/segfault.png)

---

### Post by tgalati4 on 2010-06-27
That's bad.  Not enough RAM perhaps?

---

### Post by Lyos on 2010-06-28
Could be, though it happened on both of my machines, that I tried running the program on.  One has 2-gigs of memory and the other has 4-gigs.

Any suggestions?

---

### Post by bumanie on 2010-06-28
This link may hold the key to your issue or at least give you some ideas.
[http://www.psychocats.net/ubuntucat/photorec-saves-the-day-again/](http://www.psychocats.net/ubuntucat/photorec-saves-the-day-again/)

---

### Post by meteors on 2010-11-07
how to do *ddrescue*

---

### Post by Skapunker on 2011-01-25
I was getting the segmentation fault error every time as well.  Contacted the programmer and he said it was fixed.  I'm running 6.12 and so far so good.  Here's the reply:

This issue is known and fixed since 2009
[https://bugs.launchpad.net/ubuntu/+source/testdisk/+bug/405013](https://bugs.launchpad.net/ubuntu/+source/testdisk/+bug/405013)
Try PhotoRec 6.11.3 or 6.12-WIP

wget -N [http://www.cgsecurity.org/testdisk-6.12-WIP.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.12-WIP.linux26.tar.bz2)
tar xjf testdisk-6.12-WIP.linux26.tar.bz2
cd testdisk-6.12-WIP
sudo ./photorec_static

---

