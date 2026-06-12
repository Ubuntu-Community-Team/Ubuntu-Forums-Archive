---
title: "Webmin + Squid -&gt; Redirect first HTTP request to local page?"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by gexcko on 2007-11-04
I'm running a semi-public lan in a guest house. Guests may connect wirelessly to the LAN and use the internet through it.

I'm trying to set up a redirect (as on a wireless hotspot) so that when clients to any of the access points, their first request to any website (using HTTP or HTTPS) will be redirected to an internally hosted page. This is to display rules for usage, notices, etc. Any subsequent requests will be handled normally until the client disconnects & reconnects to the network.

I'm hosting DHCP on an internal ubuntu server, using webmin to manage it. I've read that using Squid (and possibly an internal DNS server) I can accomplish this, however I haven't been able to find any instructions on how to set it up.

Has anybody done this, or know how? Any help would be appreciated.

---

### Post by g4me0ver on 2008-05-13
Anyone found an answer to this?? please!!??

---

