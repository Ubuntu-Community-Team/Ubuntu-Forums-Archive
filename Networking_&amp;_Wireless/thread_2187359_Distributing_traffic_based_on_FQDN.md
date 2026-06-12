---
title: "Distributing traffic based on FQDN?"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by cokesmoke on 2013-11-11
Hi,
I'm in the process of redesigning my home network, and are planning to setup quite a few servers in my home. Both myself and my roommate have several FQDNs configured towards the network and use quite a few ports for several uses (HTTP, IMAP, SMTP, RDP etc), but it's proven rather hard to administer as we require the use of the same ports for several domains. So I've been checking if our router (Sonicwall) can handle splitting up the traffic based on the FQDN that were used to request access, but that proved impossible, so the next shot is a server distributing based on the same criteria.

We have about 10 machines running server OS of some sort (some windows and some linux) and 3 workstations so it's not really a problem if we have to use a deticated server for this.

Anyone know how to do this, or have some other idea for how this can be solved?

---

### Post by TheFu on 2013-11-12
For the web traffic, use a reverse proxy ... I use nginx.  Fairly easy to setup.
For the other stuff, as long as they listen on different ports, the firewall can handle it.
I found it easier to get multiple IPs from the ISP - got 5 for $15/month.

BTW, RDP without a VPN is crazy, non-secure.  Setup openVPN on port 443 if you travel, since many businesses and hotels block all ports except the most popular 6 or so.  I've been burned when overseas where the hotel blocked random ports (ssh) and the default openvpn port.  The only port that seems to be allowed everywhere is 443.  That can put a damper on your HTTPS needs - I've read that some clients can support a reverse proxy for different protocols on the same port, but it depended on the clients used too ... so basically 80% of the clients didn't work. It has been a few years. Perhaps that is better.  The multi-use for 443 is why I got more IPs.

---

