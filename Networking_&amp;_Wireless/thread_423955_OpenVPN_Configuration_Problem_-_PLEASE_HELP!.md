---
title: "OpenVPN Configuration Problem - PLEASE HELP!"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by jcws6 on 2007-04-26
I'm having trouble with a basic OpenVPN (static key) problem.  I'm trying to access VPN over TCP port 443, which is port forwarded on my router & enabled thru Firestarter.  I changed the log verbosity to "6," so I can get a better picture of what's going on.

When I try to connect over VPN thru work, I get this in the client log:
Thu Apr 26 11:25:50 2007 us=336172 WARNING: Bad encapsulated packet length from peer (21331), which must be > 0 and <= 1548 -- please ensure that --tun-mtu or --link-mtu is equal on both peers -- this condition could also indicate a possible active attack on the TCP link -- [Attemping restart...]
Thu Apr 26 11:25:50 2007 us=336204 Connection reset, restarting [0]

I have tun-mtu set to 1501 on both client & server, so I'm not sure what's going wrong.  Please help!

---

### Post by jcws6 on 2007-04-26
Just stripped my server & client OpenVPN config files down to the absolute bare minimum.  Same problem.  HELP!

---

### Post by jcws6 on 2007-04-29
Bump

---

