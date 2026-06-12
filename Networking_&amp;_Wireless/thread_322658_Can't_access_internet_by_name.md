---
title: "Can't access internet by name"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by dirtmover on 2006-12-20
Ubuntu 6.06, ok this is my first linux install and I though it was all going too well. I am having some problems with internet access and name lookups.

I am connected through a Dlink DI-524 router and starbridge DSL modem.

Symptoms:
Updates don't work
Firefox doesn't work properly with name lookups i.e. [www.yahoo.com](www.yahoo.com) doesn't work

What I can do:
Access the router and modem with firefox
Ping internet using IP and name lookups
Access web pages using IP i.e. ping google.com to get the IP address to enter in firefox
The same hardware setup works fine with windows

My DNS is the address of the router (192.168.0.1) which is the same as windows.

I've done a lot of reading and tried a many of the suggestions for similar symptoms but nothing works :confused:  so I'm open to suggestions before I throw the towel in.

---

### Post by Iowan on 2006-12-20
[http://ubuntuforums.org/showthread.php?t=321181]("http://ubuntuforums.org/showthread.php?t=321181")
This thread discusses similar problems - perhaps you.ve already seen it.
IPV6 *might* be responsible, or the **resolv.conf** file... link (and contained link) discuss both.

---

### Post by dirtmover on 2006-12-21
Neither of the suggestions in that thread work. I have, however managed to get Firefox to work by turning ipv6 filter on, see [http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

I still cannot get updates/downloads to work.

Any ideas???

---

### Post by dirtmover on 2006-12-23
Fixed.:)  I was terminating the PPPoE session in the modem I switched the modem to bridge mode and now terminate the PPPoE session in the router. Everything now works as it should. I have also been able to turn ipv6 back on in Firefox. I'm guessing the modem was screwing things up.

I just wanted to close on this in case it helps others.

---

