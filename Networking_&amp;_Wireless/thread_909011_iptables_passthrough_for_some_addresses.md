---
title: "iptables passthrough for some addresses"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by knorr.orange on 2008-09-03
I am trying to allow a few specific clients to access our router directly, without going through our ubuntu proxy server.  Reading around, it seems this should be easy with iptables, but I have not managed to get anywhere with that.  Here is our setup:

switch ----> proxy server ----> ISP router

The proxy server is running Ubuntu and has two NIC's: eth0 and eth2, with eth0 facing the internal network (ip of 192.168.0.1) and eth2 facing the router (ip of 192.168.1.2)

I want to have a few machines that are allowed direct access to the router, without having to go through the proxy server (specifically squid.)  So I just want the packets to go through the server from eth0 to eth2.

My latest attempt with iptables looked like this (trying for just one machine for now):
sudo iptables -A FORWARD -i eth0 -s 192.168.0.99 -p all -o eth2 -j ACCEPT

...which of course did not work.

I would appreciate a little help with this, as I've never done anything with iptables before.

Thank you.

---

