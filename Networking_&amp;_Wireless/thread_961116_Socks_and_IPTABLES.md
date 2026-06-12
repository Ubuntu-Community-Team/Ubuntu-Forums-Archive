---
title: "Socks and IPTABLES"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by tacidsky on 2008-10-28
I have a problem that I have been looking to solve for a long time, I finally figured out what I need but I have tried and I did it wrong.

What I wish to achieve is to basically build a firewall computer,

here is a basic network picture

Computers(End Devices) - > Router -> [THE FIREWALL] -> NETWORK

What I have on [THE FIREWALL] is two network cards, one hooked to Router and one hooked to NETWORK/internet.

I need to socks5  all my traffic going through the firewall to another server on the network(One I can SSH to and SOCKS5)

I have looked up Iptables and it seems like I need to make the correct chains in order to do this, but I am lost at this point. 

The Firewall is running Ubuntu 8.04 Desktop right now but I can install anything on it so that should not matter.

---

