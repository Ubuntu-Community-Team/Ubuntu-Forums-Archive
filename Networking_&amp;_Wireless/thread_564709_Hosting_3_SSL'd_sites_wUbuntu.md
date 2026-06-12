---
title: "Hosting 3 SSL'd sites w/Ubuntu"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by mikecrowe on 2007-10-01
Hi folks, 

I want to support 3 unique SSL'd sites on my ubuntu box.  They are all subdomains of an existing domain:

d1.mydomain.com
d2.mydomain.com
d3.mycomain.com

All only support SSL (so all are coming into :443).  Due to the nature of the application, I'm not opening port 80.

We have a T1 line coming in, and 8 IP addresses assigned to us.  I'm using a Netgear VPN to connect to the T1.

I'm starting to sense that you can't do SSL based Name-Based virtual hosting.  Is that right?

n00b question:  If that is true, I can designate each SSL site to a different IP address.  If I use the Netgear to forward all :443 requests to Apache, will it see the different IP address and respond accordingly?

TIA
Mike

---

### Post by noob12 on 2007-10-01
It should work if you set up virtual interfaces for all of the desired  addresses (assuming they are all on the same logical subnet).  Can't help with the Apache configs though.

---

