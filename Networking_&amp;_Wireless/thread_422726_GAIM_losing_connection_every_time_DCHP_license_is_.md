---
title: "GAIM losing connection every time DCHP license is renewed"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by ocdude on 2007-04-25
Approximately every 24 minutes, my computer renews it's DCHP license with the main router and I lose connection to the AIM service through GAIM. I have in my dhclient.conf file changed how long the lease is supposed to be, but it gets superseded by the router that I connect to.

I have no access at all to the router as I am on a university network, but this is driving me nuts as AIM is my only form of communication with the rest of my group (it's a complicated story).

Is there any way that I can prevent this from happening, short of actually having to go to the router itself and requesting a longer lease time? I don't have a static IP, but my address does not change every time I get the lease renewed.

This affects my Yahoo! connection through GAIM as well, but not as often. It also affects connection to those services through Kopete, and weirdly enough, through Meebo, the online IM client (run through firefox). My other network services seem to work fine, for the most part. Every so often port 80 requests (via firefox or any other browser) also go weird and take a long time to resolve DNS. I thought the domain name servers on this campus might be the problem so I switched to using OpenDNS, but this hasn't really solved the IM problems, only some of the browsing problems. I'm totally confused. :confused:

---

