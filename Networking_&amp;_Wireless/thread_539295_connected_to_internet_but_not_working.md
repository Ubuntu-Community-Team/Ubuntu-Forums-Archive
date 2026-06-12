---
title: "connected to internet but not working"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by djackpot on 2007-08-31
Hey

I know there are several different posts about this kind of problem but I think it s related to the hardware, this is why im posting..

So I installed ubuntu yesterday, and internet worked fine so that i could up date it with a huge 140 files update. After this, the internet connection just stopped being useful, sometimes i could actually get connected but with no loading at all

I m running ubuntu 7.04 i guess my wireless card is  usb zd1211 tested with zd1211rw and zd1211rw-80211

I have already tried to do a lot and you can follow the evolution here : 

[http://paste.ubuntu-nl.org/35741](http://paste.ubuntu-nl.org/35741)           [http://paste.ubuntu-nl.org/35742/](http://paste.ubuntu-nl.org/35742/)       [http://paste.ubuntu-nl.org/35747/](http://paste.ubuntu-nl.org/35747/)           [http://paste.ubuntu-nl.org/35748/](http://paste.ubuntu-nl.org/35748/)     [http://paste.ubuntu-nl.org/35751/](http://paste.ubuntu-nl.org/35751/)        [http://paste.ubuntu-nl.org/35754/](http://paste.ubuntu-nl.org/35754/)

basically I changed of kernel to the previous one with no result and i blocked a driver enabling another one with no result either.
 

Please help...

---

### Post by djackpot on 2007-08-31
please I have been stuck with this problems for days now, I would really appreciate some advices...

---

### Post by Rui Pais on 2007-09-01
hi,

from [this log]("http://paste.ubuntu-nl.org/35742/") of yours it seems that avahi-daemon is preventing dhcp to set a (correct) IP to your net card,  

May i suggest you try this:
```
sudo update-rc.d -f avahi-daemon remove
```

and after that reboot.

Good luck.

---

### Post by Kzap333 on 2007-09-23
I think I have the same problem HELP NEEDED.

---

