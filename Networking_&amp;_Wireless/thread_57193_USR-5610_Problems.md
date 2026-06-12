---
title: "USR-5610 Problems"
date: 2005-08-15
forum: Networking &amp; Wireless
---

### Post by TheGMan on 2005-08-15
hi,
i have installed a fresh ubuntu and have tried to get my modem to work (USR-5610b). in windoze it specifies com3 so i have configed pppconfig for /dev/ttyS2 (correct?) and ive also tried /dev/modem as well as most of the others. 
i have used scan modem and some various other tools. they can all see the modem. i have also used pon at the terminal and it hasnt worked...the log says: 
```
Aug 15 15:23:42 localhost pppd[20190]: pppd 2.4.2 started by ben, uid 1000
Aug 15 15:23:43 localhost chat[20191]: Can't get terminal parameters: Input/output error
Aug 15 15:23:43 localhost pppd[20190]: Connect script failed
Aug 15 15:23:44 localhost pppd[20190]: Exit.
``` 
......any ideas?? 
btw USR site has a RPM of drivers but a friend of my reccomended against them...think it would screw things over if i did use the RPM?

---

