---
title: "Compaq r3000 with broadcom wireless"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by tieflingrogue on 2008-01-08
Hi!  I'm  trying to get wireless working on a Compaq r3000 with broadcom wireless.  Ubuntu 7,10 is installed.

I've installed wicd and can see my wireless network listed in the wicd network manager.  However when I try to connect the message is "Obtaining IP address...".  It does this for a while and stops with no connection. 

 I've disabled security on my network, so that shouldn't be a problem.  Also my network "light" is on so I guess the card is working somewhat, just can't seem to connect to the network.

Also, before I tried  wicd I was using the default network manager.  My wireless network was also found using network manager, but again still couldn't connect. 

I've attached a screen shot of the wicd manager trying to connect.
thanks,

---

### Post by luisromangz on 2008-01-08
If you are using the bc43xx driver, you should give ndiswrapper a try, it works better for me.

---

