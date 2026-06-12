---
title: "Static IP problem"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by peterthewolf on 2008-11-03
This should have been added to a past post but the Intrepid test and install sub forum has been closed. A proper Simpson DOH

Anyway if you are having problems with static IP on intrepid I have found that if you dump network manager and install WICD instead then the problems disappear.

Google "wicd" for instructions.

Since fiesty this piece of software has been rescuing network manager, albeit mainly with Wifi, BUT it is still not in the repositories by default.

Once you have used it you will understand my bewilderment that gnome perservers with Network Manager when this exists.

---

### Post by The Cog on 2008-11-03
Another vote for wicd here. I think it's great and don't understand why the Ubuntu devs chose NM instead.

Another problem with network-manager is that it doesn't work unless a GUI user is logged in. No use for leaving the lappy on as a server. wicd on the other hand both works before a user logs in, and does static IP addresses nicely.

---

