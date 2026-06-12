---
title: "can't see ubuntu in windows networked computers"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by roop_s on 2007-12-08
after doing a few searches that have come up empty, i'm gonna take the easy route and just ask.

the network is up and running. there's a permanently mounted windows share on the ubuntu system that works great. however, on the windows computer in the workgroup the ubunut system doesn't show up.


i totally forgot what to do in this situation. i believe there's a single command i need to type to turn on some kind of broadcasting but i forget what it is. anyone know?

---

### Post by maher_79 on 2008-02-28
I am having the same problem.  I can see windows computers on the network but can't see my ubuntu folder that i've shared!

Can anyone help plz?

---

### Post by Eiríkr on 2008-02-28
This is because sharing goes two ways.  Windows is quite promiscuous in this regard, and happily broadcasts its availability across the network.  Ubuntu, on the other hand, is a bit more circumspect, and while you can easily receive a share, you have to deliberately set your computer up to *serve* a share before your Ubuntu machine will announce that it has something to share.  

The Windows-compatible sharing app on Linux systems is called Samba.  Configuration can get quite complicated, but Ubuntu apparently has some nice GUI tools to streamline the process.  I only have Xubuntu myself as a file server, which is a pared-down version of Ubuntu without some of the GUIness, so unfortunately I cannot walk you through the simplest setup.  But try searching the forum for "samba sharing" or something similar, and you should find plenty of information.  

Cheers,

Eiríkr

---

