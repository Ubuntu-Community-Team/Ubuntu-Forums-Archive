---
title: "How to setup dedicated network card for VOIP conenction to ISP with different ip,dns."
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by rrozman on 2008-03-19
Hi,

I have possibility to connect directly to ISP's VOIP SIP server, but do have to use dedicated network card, cause they need to write it' s mac in their dhcp database. I have already two network cards used to firewall/nat setup for my LAN (I'm using LMCE). Now I'd like to add this third card (eth2), but would not like to break anything with my existing network setup.

I've tried simply with :
auto eth2
iface eth2 inet dhcp

in /etc/interfaces but it seems that eth2 takes over my networking (it gets its IP right, but also changes DNS and gateway settings - but it's entirely on other numbering range 10.xx.xx.xx) - and my networking setup stops working.

I don't know anything about how to properly setup this card, so probably I will spit some funny statements here...
I'd like to use that eth2 connection solely for Asterisk to register with my ISP's SIP server and nothing else. But eth2 needs to get ip from dhcp and have it's dns setup, so I'm able to use URL for sip server registration...

Can I find any more info on how to set this up ?

Anyone with more insight how to setup such situation without breaking anything (or as least as possible) with eth0,1 ?

Thanks in advance,

regards,

Bulek.

---

