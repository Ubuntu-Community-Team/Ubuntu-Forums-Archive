---
title: "How can I make my VPN Server forward all traffic to eth0 / internet?"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by oneofthemany on 2007-11-15
I've set up a PPTP VPN server on an ubuntu gutsy box and I can connect to it fine.

My problem is, how can I forward all traffic from the vpn to the internet? (anything thats not 10.8.0.x)

My setup is as follows:

Client 10.8.0.2 (set to forward all traffic to the vpn)
        |
        | internet
        |
VPN Server ppp0 - 10.8.0.1
VPN Server eth0 - 192.168.1.120 (example ip) gateway 192.168.1.1

basically I want all traffic from ppp0 to be passed to eth0 but I cant find out how to route it or bridge them.

Could somebody point me in the right direction please?

( btw: the reason I want to do this is because the connection between the client and server is over a wireless connection which may be unencrypted or subject to being sniffed )

---

