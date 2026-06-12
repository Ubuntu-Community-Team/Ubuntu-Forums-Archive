---
title: "Help Broadcom 4318"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by dwinn86 on 2007-01-09
I've been trying for almost two weeks to get my Broadcom 4318 Air Force One to work with Edgy. I have just followed this guide: [http://tusharg.blogspot.com/2006/11/configure-ubuntu-610-edgy-on-hp.html](http://tusharg.blogspot.com/2006/11/configure-ubuntu-610-edgy-on-hp.html)
however, the script failed so I updated my kernel and ndiswrapper according to this:
[http://compwiz18.blackhole.cx/bcm4318/howto.htm](http://compwiz18.blackhole.cx/bcm4318/howto.htm)

Now when I do a ndiswrapper -l  i get the following response:
```
  bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx) 
```

However, when I do an iwconfig it lists no wireless extensions...

Any advice?

---

### Post by warkro on 2007-01-10
I think the problem is that you didn't blacklist your drivers for bcm43xx in /etc/modprobe.d/blacklist

follow this howto:
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

plug your laptop in with a wired connection... get automatix install network manager.  

Comment out everything in your /etc/network/interfaces file except the ones with LO in them. 

restart.

---

