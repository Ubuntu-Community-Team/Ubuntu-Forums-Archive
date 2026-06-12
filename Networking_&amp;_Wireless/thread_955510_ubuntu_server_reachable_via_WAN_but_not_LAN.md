---
title: "ubuntu server reachable via WAN but not LAN"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by barrettam on 2008-10-22
I have a home network made up of a Vista box, an XP box, and an Ubuntu box (hostname = capablanca).  

A ping to capablanca from the MS machines will correctly resolve the IP address, but will timeout.  

If instead I ping using the WAN address (dyndns + router port forwarding), I get a response.  I can also SSH from MS machines to capablanca via the dyndns WAN address, but not using "capablanca" as the address.

What gives?

---

### Post by Iowan on 2008-10-22
Does it work via IP address?
Might also check Winbind (winbindd) package.

---

### Post by barrettam on 2008-10-23
no, it does not work by IP address either.  Also, I'm at the latest version of winbind.

Thanks for the reply though!

---

