---
title: "UBUNTU+Openswan with Cisco ASA VPN tunnel (IPSEC)"
date: 2014-11-30
forum: Networking &amp; Wireless
---

### Post by javier32 on 2014-11-30
Hi,


I'm trying to configure a VPN tunnel with IPSEC using Openswan in my office. I have no visibility of the other side of the tunnel (Cisco ASA), but my client has provided me the parameters needed to create the connection.


Phase I is established successfully, but phase II rise the following error:


|    Notify Message Type: NO_PROPOSAL_CHOSEN
| removing 8 bytes of padding
"xxxTunnel" #1: ignoring informational payload, type NO_PROPOSAL_CHOSEN msgid=00000000
| info:  e4 83 b1 79  a0 b2 a1 85  25 ca 6c cf  09 81 86 14
| info:  d4 6d 64 71
| processing informational NO_PROPOSAL_CHOSEN (14)


As far as I understand Openswan and how I've configured it in this case, I think all parameters should be correct, but I suspect that the root cause of the problem is the networking configuration.


From my client side, I have told that I should do a port forwarding for all my network traffic (which is going to my client IPs) to a one single IP (proxy), but I don't know how exactly I can configure this...


Should I use any parameter in the ipsec.conf for this proxy configuration?, like leftnexthop, rightnexthop...


Should a SNAT (or MASQUERADE) option fix this NO_PROPOSAL_CHOSEN issue?


Any help will be welcome... thanks in advance!!


Javier

---

