---
title: "how to configure a modem in ubuntu?"
date: 2005-08-16
forum: Networking &amp; Wireless
---

### Post by TheGMan on 2005-08-16
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

### Post by cannibalbob on 2005-08-17
no one uses modems anymore? theres surprisingly little documentation for them.

---

### Post by az on 2005-08-17
[QUOTE=cannibalbob]no one uses modems anymore? theres surprisingly little documentation for them.[/QUOTE]

That is untrue.  But the fact that hardware modem typically require little configuration and the closed-source binary drivers that are needed to run software modems are not available for development to the public leaves very middle ground for anybody to work with.

If it is a hardware modem that was using COM3 in Windows, if should be /dev/ttyS2.

It may not autodetect, but it should still work.  

Try ttyS0, ttyS1 or ttyS3 if ttyS2 does not work.  Note the capital "S", too.

If it is not a hardware modem, you will ot get it to work in linux, since USR does not like to support the linux community.

---

### Post by teyster2 on 2005-08-28
[QUOTE=TheGMan]hi,
i have installed a fresh ubuntu and have tried to get my modem to work (USR-5610b). in windoze it specifies com3 so i have configed pppconfig for /dev/ttyS2 (correct?) and ive also tried /dev/modem as well as most of the others. 
i have used scan modem and some various other tools. they can all see the modem. i have also used pon at the terminal and it hasnt worked...the log says: 
```
Aug 15 15:23:42 localhost pppd[20190]: pppd 2.4.2 started by ben, uid 1000
Aug 15 15:23:43 localhost chat[20191]: Can't get terminal parameters: Input/output error
Aug 15 15:23:43 localhost pppd[20190]: Connect script failed
Aug 15 15:23:44 localhost pppd[20190]: Exit.
``` 
......any ideas?? 
btw USR site has a RPM of drivers but a friend of my reccomended against them...think it would screw things over if i did use the RPM?[/QUOTE]
 use ttyS14 worked for me.  I found this also elsewhere in this forum. You'll be able to connect.  Then use Synaptic Package Manager to down load "set serial"(change repository and add the other sites) after installing set serial do the following.  Open root terminal type: lspci -vv.  This will get your irq and address.  next type: setserial /dev/ttyS2 irq 17(mine was 17 yours may be different) port 0xd00 (substitue your port and add the 0x in front of it.  Next:  pppconfig. this will save your settings.  Hope this helps.

---

