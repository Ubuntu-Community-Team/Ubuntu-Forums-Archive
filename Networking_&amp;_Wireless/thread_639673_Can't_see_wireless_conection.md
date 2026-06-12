---
title: "Can't see wireless conection"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by agarzon on 2007-12-13
I am new to Ubuntu, and relatively new to linux. I just installed Ubuntu 7.10 on an IBM laptop (Thinkpad A21m). The installation went OK. But I am having problems getting the PCI wireless card to work.

 I checked some of the posts and didn't find anything that would fully relate.

I have a Linksys WPC54GX ver.2 Wireless G card. When plugged in, the system (device manager) sees the card (though lists a different vendor, maybe the chipset manufactrurer?)  but doesn't work and two things happen:
The wire connection goes kaput, and ifconfig does not display the wireless card... only lo and eth0 (the wired connection)

How can I get this thing working? :mad:

---

### Post by cleersf on 2007-12-13
Did you give this post a try?

[http://ubuntuforums.org/showthread.php?t=484359&highlight=WPC54GX](http://ubuntuforums.org/showthread.php?t=484359&highlight=WPC54GX)

---

### Post by agarzon on 2008-02-20
cleersf.

Thanks for the link to the other thread. 

I did tried the procedure recommended there but yielded no results. The hardware was still identified, but the card would not power up.

At the end, I got *knetworkmanager* installed and the card leds started blinking and could connect.

For me, on this particular machine, took both * ndiswrapper* and *knetworking* to get the wireless card to connect.

---

