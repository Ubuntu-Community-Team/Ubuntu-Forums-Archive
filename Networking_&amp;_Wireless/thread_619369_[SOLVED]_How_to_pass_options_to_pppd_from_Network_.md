---
title: "[SOLVED] How to pass options to pppd from Network Manager"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2007-11-21
I am struggling to get Network-Manager VPN to connect to my VPN at work. A windows XP system on the same network can connect. My Ubuntu system and the XP system both use the same Linksys wireless router. Ubuntu will not work with cabled to the router, so I do not believe this problem is wireless-based.

/var/log/syslog is showing a connection and then a disconnect. This leads me to believe, from having gotten pptpconfig to work on 6.06, that I need to pass a delay value off to pppd. Specifically, it would be connect-delay n.

I've tried to do that on the ppp options screen of Network-Manager's configure vpn, and that is causing the connection to fail while checking the syntax.

How can I pass parameters to pppd from Network Manager?

---

### Post by cmnorton on 2007-11-21
I can pass a connect delay through /etc/ppp/options.pptp

---

