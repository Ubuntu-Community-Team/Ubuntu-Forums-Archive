---
title: "Wifi not connecting - network seen"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by ahickey on 2007-04-11
Hi,

I installed Ubuntu 7.04 (Feisty) and it detected my PCI Wifi card an Edimax EW-7128g (I think) RT61 chip set.
When I rebooted it detected the wifi card and even detected by wifi network as it was in the list of networks available.

If I run ifconfig - a  ra0 is listed as being an adapter

When I selected my wifi network it tries to connect but fails.

I used the LAN connection on my motherboard and it worked perfectly, so I know the DHCP server is working.
I disabled the onboard LAN to only have the wifi and this made no difference.
At the moment for testing I have no encryption on my wireless network.  
Plan is to put that in place after I have everything working.


Any/all sugestions welcome.

---

### Post by josephus on 2007-04-11
have you tried

sudo ifdown ra0
sudo ifup ra0

to try to bring the interface up.

can you post iwconfig, iwlist scan, and lshw -class network

---

### Post by Gina on 2007-04-11
That's interesting - I too have been having problems with Feisty and wifi card though mine's a different one.  (As posted in a couple of other threads). Ping didn't work but I've just tried ifdown amnd ifup and ping now works :)

Now to see if I can get any further...

A little later...  Eureka!!  It all works now :):)  Thank you very much for the suggestion :)

---

