---
title: "Freenx with dynamic IP"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by BiggoCharley on 2007-08-04
I have installed the freenx server on my ubuntu dapper box and the client on my dapper laptop. I am trying to configure the desktop server to use a dynamic dns service to update my ip when it changes. My question: does the server hostname have to be a registered domain name in order to get my ip to update.  I'm using zoneedit.com which I have used for a long time for website ip updating with no problems.

---

### Post by smileypaul on 2007-08-04
Hopefully im understanding you properly here..

In short, no.. the server hostname does not need to be a registered domain name. The hostname can be anything you like, its generally just the name of the box.

Usually you with ddns , you just register with company, update the info, and whenever someone tries to access yourdomainname.zoneedit.com using whatever service, it is re-routed to your ip address.

hope that helps,

Paul

---

