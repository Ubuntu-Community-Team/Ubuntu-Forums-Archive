---
title: "Multicast requests on a separate interface"
date: 2015-12-03
forum: Networking &amp; Wireless
---

### Post by bryan58 on 2015-12-03
I have 3 nics. eth1 is for internet traffic.  eth3 is for multicast traffic not coming from the internet.  The multicast traffic is INCOMING.  When I make a multicast request using VLC, I am unable to pull the stream.  I know the problem lies with the default route.  When I turn eth1 off, (eth2 is not in use), and allow eth3 to become the default route, I am able to pull the multicast stream in VLC.  How do I route all incoming multicast traffic to eth3 and allow multicast requests to go out eth3 as well?

I tried adding to /etc/network/interfaces/
post-up route add -net 224.0.0.0 netmask 240.0.0.0 eth3

with no success.

Thank You
Bryan

---

