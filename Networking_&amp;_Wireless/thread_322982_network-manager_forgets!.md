---
title: "network-manager forgets!"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by Coburn on 2006-12-21
Ive got 2 Dapper computers hooked with a wire.  We use dialup, and sometimes I want to switch and connect directly from the other computer to the Internet.

What I tried to do was set up different locations in network-manager.  Let's call them server and client. :) :cool: 

Server has the modem configured with ISP and password, etc.

Client has ppp0 not configured at all.

When I start up network-manager, it goes to the blank configuration, which is actually what I was using last.  It does not display the name of the last location.

When I switch from client to server, the modem remains unconfigured.

In other words, the network-manager did not save my settings! :confused: 

BTW I posted this as a bug and still haven't heard...

Any suggestions?  What's the old way to do this?  What files am I using behind the scenes?

Thanks

---

### Post by MihaiM on 2006-12-24
Network Manager also deletes my static IP configuration. After a random (short) period of time the IPs just disappear. After I remove network manager and restart the computer the IPs work again.

---

