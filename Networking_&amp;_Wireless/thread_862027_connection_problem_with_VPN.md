---
title: "connection problem with VPN"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by juliank on 2008-07-17
Hello!

I've a problem with my wireless connection via VPN.
The goal is to connect to the network of my university which is secured by Cisco VPN. The installation of the Cisco VPN-client worked well.
The connection can be established, but my browser doesn't open any website.
(I tried with Firefox 3.0, Opera 9.50, Link2, Epiphany 2.22.2)
I can ping other websites, so i think that the connection is okay.

But I've no idea where the problem is. Can someone help me?

kind regards
 Julian

_edit_: Problem solved!
I had to edit the resolv.conf. The nameserver was missing.

---

