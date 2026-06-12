---
title: "connection using wan miniport PPPOE"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by smarthmd on 2006-09-16
hi there i've installed ubuntu os recently n i don't know how to connect to internet using my broadband. letme tell u how i connect in windows. i go to network connection n select make a new connection. then in it i select connect to net using wan miniport PPPOE n then i enter username n password given to me by bsnl. how do i connect to net in ubuntu?? please reply

---

### Post by drakshug on 2006-09-16
If you are not on a static ip
terminal
sudo pppoeconf 
follow the instructions

or get rp-pppoe (if you have another box with a connection)
Good luck. My wan miniport works fine on widoze but only works after a fresh install on dapper.

---

