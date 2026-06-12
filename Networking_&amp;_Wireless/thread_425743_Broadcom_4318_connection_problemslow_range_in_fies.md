---
title: "Broadcom 4318 connection problems/low range in fiesty"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by pgunsul on 2007-04-27
Hello all,

I performed a clean install of fiesty on my Dell laptop (I was running Dapper for a year before that) and I have had sporadic results with my wireless connection.  If I am sitting right next to the wireless router, the laptop connects wonderfully (I connect using bcm43xx and network manager which I am very happy that it's working at all with what I have been reading on this forum!)

However, if I try to connect in the living room, I lose the connection.  I dual boot my laptop and windows xp has no problem connecting from the same location.  In fact, none of the wireless devices (Wii, Tivo, etc.)  have problems connecting since I live in a small apartment.  Also, this problem seems to have arisen since installing fiesty since wireless was working fine (with some tinkering with ndiswrapper) in Dapper...

Is this just a driver issue with bcm43xx?  or is there something that I could do to improve the connection range?  

Any ideas are appreciated!

-Paul

---

### Post by spd106 on 2007-04-29
Hi,

There are transmission power related problems with the bcm4318 at the moment. See [http://linuxwireless.org/en/users/Drivers/bcm43xx](http://linuxwireless.org/en/users/Drivers/bcm43xx)

Hopefully the issue will be resolved for the next release (7.10), for now all I can say is to try using ndiswrapper instead.

---

