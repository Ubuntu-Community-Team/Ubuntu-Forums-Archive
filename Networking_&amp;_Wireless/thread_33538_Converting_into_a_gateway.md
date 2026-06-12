---
title: "Converting into a gateway"
date: 2005-05-11
forum: Networking &amp; Wireless
---

### Post by maitredede on 2005-05-11
Hello

I have a current install of Hoary with 1 network card on a server behind a hard gateway (DI604). The problem is, I can't get full bandwidth with connections between Inet and my server. It's a game server (with other servers like samba) but players keep complaining about high ping.
So I'd like to remove my DI604, add a net card on my server to make it directly connected on Inet, and acting like a gateway.

So i'd like to know how I can make Hoary become a classic gateway (firewall, NAT, and the game server directly connected to Inet).
Since I'm some kind of noob with linux, where can I find graphical tools to configure the gateway functions, firewall open ports, port forwards...

---

### Post by mindspin on 2005-05-11
I know none like this, but maybe fwbuilder could help a bit...


mindspin

---

### Post by az on 2005-05-11
Firestarter should suit your needs.

Otherwise, shorewall and dnsmasq.

---

