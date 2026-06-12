---
title: "remote access and firewalls"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by boondocks on 2008-01-23
My uncle Bob has a Ubuntu 7.10 desktop.
He is sitting behind a campus-like firewall.
He has no control over the firewall.

Can the following remote access be done:
a.  Bob initiates the remote access session.
b.  It goes thru that firewall with keep-alive, etc.
c.  It comes to my desktop (Ubuntu or XP).  I control my firewall.
d.  I connect to his Ubuntu 7.10 desktop (and show him how to use OpenOffice).


At the moment:
We have Remote Access enabled on his Ubuntu 7.10 desktop.
But I cannot connect to his desktop because his firewall is blocking me out.

---

### Post by sqrt2 on 2008-01-23
The university most likely filters on new incoming connections because it isn't expected that a normal workstation provides services to the Internet. (This assumption probably even is a key element in their security concept.) What you could do is set up a VPN server on your machine. Bob will connect to your machine and you will have a unfiltered virtual network where you can open new connections to Bob's PC. The link from Bob to your machine will be encrypted.

OpenVPN is relatively simple to set up. You should check whether the university's Internet use policy allows using tunnels to another machine, though, because otherwise the whole procedure can get Bob's Internet connection shut down. (It may be possible to make all the traffic look like normal HTTPS traffic, but still, you're effectively subverting the university's security policy and you should talk to the network administrator first. He'd probably even agree to simply treat Bob's PC different from all the others which would make the whole VPN thing unnecessary.)

---

