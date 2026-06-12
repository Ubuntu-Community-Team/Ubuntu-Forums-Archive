---
title: "Internet Not Working Anymore"
date: 2005-03-30
forum: Networking &amp; Wireless
---

### Post by The Oil Crisis is Here on 2005-03-30
Hi everybody!

I have had Hoary working fine with my adsl modem via ethernet for a month or two now. I havn't had any problems with it until the other night. I unplugged the modem and ran it with my laptop (also running hoary) to update some packages, and when I plugged it back in to my desktop computer it wouldn't connect to the internet. I have tried deactivating and reactivating it under network administration without any luck. I know there is no hardware issue as the computer hooks up fine when I run my Damn Small Linux rescue disk. Any ideas out there on how to fix this problem??

Cheers. 

 ](*,)

---

### Post by ming0 on 2005-04-03
Have you tried going to a console and typing: 

 ```
sudo dhclient eth(your interface)
```

That might help?

---

### Post by sfw5000 on 2005-04-05
You might also try 

sudo ifdown eth0

and then

sudo ifup eth0 

and see what kind of output you get -- it should tell you if there is a dhcp problem or something... also post your ifconfig -a so we can see what that says.

---

### Post by arctic on 2005-04-05
the dhcpclient script was buggy after the last updates (they forgot to add a comma). there are various topics on this in this forum. please use the search tool. ;)

---

