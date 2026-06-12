---
title: "PPTPConfig VPN"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by rotten777 on 2006-12-13
I've got a VPN setup at my corp office and VPN in using a profile in pptpconfig's package. I connect and I see a route added in my routing table but it is an incorrect route.

I have to manually enter:

sudo route add -net 192.168.1.0/24 ppp0

And this brings up the VPN's LAN.

Any tips on either fixing the pptpconfig's profile or automatically running the route add command upon the connection coming up?

---

