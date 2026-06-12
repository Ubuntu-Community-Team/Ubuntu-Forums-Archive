---
title: "Use Privoxy to do HTTP-Tunneling ?"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by mpa on 2005-11-14
Ever since my ISP requires every connection to go through their proxy I can no longer use IRC, Bittorrent or even Email POP. Http is about the only protocol allowed by the server. So I've been thinking, could privoxy allow me to use other protocols by tunneling them through http ? If yes, how ?

I managed to install and configure privoxy, but only http currently works.  I really am not sure how to configure the forwarding of socks 4.

I tried :

forward-socks4a   /              localhost:8118 .

but it messed up everything. Is there anyone experienced in privoxy willing to help me ? Thanks in advance.

---

### Post by ngms27 on 2005-11-15
This isn't right. Proxies generally only proxy HTTP, HTTPS, FTP

Other protocols will not use the proxy, but will use normal IP connectivity to connect to the remote.

I would ask the ISP if they are filtering the other protocols as its nothing to do with you configuring a Proxy on your browser.

JonnyT

---

