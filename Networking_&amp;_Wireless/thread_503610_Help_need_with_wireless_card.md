---
title: "Help need with wireless card"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by 555 on 2007-07-18
hi, i've installed ubuntu on my laptop and managed to install most things i want so far but i can't get my netgear wg511 v1 card working. On the supported list page it says it works out of the box but i can't connect also the green light is on but the yellow one is very dim but flashing fast or flickering. Wired works straight away fine. I've search on here and found a few topics with people having issues on wg511 v1 and v2 and possible sollutions but not really sure. 

how can i get it working so it works like it does on xp or like wired does? thanks

---

### Post by kevdog on 2007-07-18
I think this card uses atheros drivers, but Im not sure.  Can you post the following:
lshw -C network

---

### Post by 555 on 2007-07-18
i thought that was v2 of the WG511 and that v1 which i have used prism drivers? It does mention Prism in terminal after that command but i will post it up when i connected it to the router as i'm using the connection right now on another pc. 

after reading another post on here i searched for i've now tried installing ndiswrapper and the drivers ngwg511.ini etc which i took from a windows machine and put in my home folder, also i followed the instructions and installed Wicd but still i can't get it working, however the green light now flashes slowly instead of being constant and there is no yellow light at all now. I feel xp is inevitable as i need wireless on latop. :(:(

What i tried was posted by tl300 about half way down on this page as it seemed to work for others. 

[http://ubuntuforums.org/showthread.php?t=421526&page=2](http://ubuntuforums.org/showthread.php?t=421526&page=2)

---

