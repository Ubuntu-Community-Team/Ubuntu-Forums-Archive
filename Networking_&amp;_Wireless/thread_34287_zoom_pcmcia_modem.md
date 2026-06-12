---
title: "zoom pcmcia modem"
date: 2005-05-14
forum: Networking &amp; Wireless
---

### Post by ntlnsideidiotoutside on 2005-05-14
having problems with dial up modem, the modem is a zoom pcmcia 3075-L model.
it should work with linux its not a soft modem, i can dial the isp but it dies right after.
(error 10)
i contacted zoom and they confirmed that its a linux compatible modem.


anyone else with  this model? 

thanks
 :-?

---

### Post by nullpointer on 2005-05-27
I have a Zoom 3075 (not sure about the L bit, though) and fought through exactly the same problem you are having. 

In my case, the modem wasn't being initialized properly--that is to the liking of the ISP's terminal equipment, which is picky, picky, picky. I also had the same problem with a USR Sportser external modem.  There are two potential fixes:

1. Have the dialer issue a reset-to-defaults command. Try all of the following: ATZ, ATZ0, ATZ1, ATZ2.  Edit the dialer script to eliminate any other modem initialization strings. 

2. Presuming the modem works in Winders, open the dialer window so that you can see how the Redmondians initialize the modem.  You will probably note two initialization strings, one long, and one beyond belief.  :-? 

Duplicate these in your linux dialer, eliminate all other init strings, and everything should work.

Method one worked for my USR Sportster and method two worked for my Zoom 3075. You may need a dialer that can issue two separate init sequences. I did and turned to wvdial.  Read the man page if you are not familiar with it.

Good luck.

N.P.

---

