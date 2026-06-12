---
title: "BCM4306 Rev 03 Problems and soultion with 6.10"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by dabone on 2007-03-03
I have been trying all day to get the integrated 4306 working in a gateway laptop.
I've tried 6.10.

The bcm43xx drivers worked fine with a Belkin F5D7010
card (4318 rev 02) but would not work with either 4306 rev 03 cards I have here.
(one came with the Gateway m520, the other is in a Dell Inspiron 5150)
I tried all the tricks of locking it down to 11mbs and manually setting channels and ap, but could never get it to connect to the ap.


Then I installed bcm43xx-firmware from this source.


deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego bcm43xx


Internal nic now works fine.


Nic shows up fine and configures for wep 64 bit just fine. (Don't laugh I have kids with nintendo ds's and a psp)

Thanks to cafuego for a good set of firmwares.

I tried the gateway drivers, the dell drivers, the default script for firmware installs and nothing.. 

Hope this post helps the new person.


Later,
dabone

---

### Post by gcmacarth on 2007-03-13
hi there. I am having issues with a 4306 as well. once downloaded, i ran the deb installer.  what on earth am i to do afterward?  

thanks in advance

---

