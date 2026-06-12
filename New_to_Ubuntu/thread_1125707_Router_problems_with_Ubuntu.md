---
title: "Router problems with Ubuntu"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by jggard on 2009-04-14
Hi,

I'm new to Ubuntu and looking for some help concerning router issues.  I have a cable modem connected to a Belkin wired router, which is connected to an XP machine and the Ubuntu one.  

The connection works if the cable modem is connected directly to Ubuntu, and the router works fine with XP, which required no setup.  Now I'd like to get the router working with my Ubuntu machine as well.

The first thing I tried was switching from Network Manager to Wicd, but still no luck.  The router documentation claims its OS independent.  Also, I can access the router setup ([http://192.168.2.1](http://192.168.2.1)) from the XP machine but not Ubuntu.    

Can anyone please give me some suggestions on how to get this working?  And, if possible, not too complicated please.  

Thanks.

---

### Post by halitech on 2009-04-14
with the Ubuntu computer connected to the router, open a terminal and post the output of
```
sudo ifconfig
```

---

### Post by Iowan on 2009-04-14
**sudo ifconfig** will reveal much...
 DHCP or static addresses? If DHCP, which box is DHCP server? If Ubuntu gets IP address (hopefully not 169.254.X.X), can it ping router?

---

