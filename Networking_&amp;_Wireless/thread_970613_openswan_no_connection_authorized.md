---
title: "openswan: no connection authorized"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by piusvelte on 2008-11-04
I started out setting up asterisk and can make voip calls between my phones inside my network. Asterisk acts as a proxy for making calls over sip, so finding the recipients outside the network requires more work. As a solution, I've been trying to set up openswan to tunnel my phones in. I've been reading about how difficult l2tp/ipsec can be to setup, but I'm hoping someone can help me out.

The vpn server is sitting behind a d-link dir 655 router, which is vpn aware. I'm forwarding tcp and udp on ports 500, 4500, 1723, 1701, and traffic types 47 and 50. There's probably a few there that I don't need, but I've read varying stories on this. The router uses the term 'traffic type', which I hope means protocol and is why I'm forwarding 50. I also read about someone using type 47, so I punched that one through also.

I setup a ca, and create some certs. I started out trying PSK, but read that openswan won't make connections with dynamic clients using PSK.

Here's my ipsec.conf:

```

version 2.0

config setup
 interfaces="ipsec0=eth0"
 #interfaces=%defaultroute
 nat_traversal=yes
 virtual_private=%v4:192.168.0.0/16,%v4:10.0.0.0/8,%v4:172.0.0.0/8
 plutodebug=all
 plutostderrlog=/var/log/pluto.log

conn %default
 auto=add
 authby=rsasig #secret
 type=transport
 forceencaps=yes
 pfs=no
 keyingtries=3
 compress=yes
 disablearrivalcheck=no
 left=192.168.1.2
 leftsubnet=192.168.1.0/24
 leftnexthop=192.168.1.1
 leftprotoport=17/%any #1701
 leftcert=caracalla.pem
 leftrsasigkey=%cert
 right=%any
 rightsubnet=vhost:%no,%priv
 rightprotoport=17/%any

# disable opportunistic encryption
include /etc/ipsec.d/examples/no_oe.conf

```

And the log file:
```

packet from 66.227.95.240:181: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 0
0000004]
packet from 66.227.95.240:181: ignoring Vendor ID payload [FRAGMENTATION]
packet from 66.227.95.240:181: received Vendor ID payload [draft-ietf-ipsec-nat-
t-ike-02_n] method set to=106
packet from 66.227.95.240:181: ignoring Vendor ID payload [Vid-Initial-Contact]
| nat-t detected, sending nat-t VID
| find_host_connection called from main_inI1_outR1
| find_host_pair_conn (find_host_connection2): 192.168.1.2:500 66.227.95.240:181
 -> hp:none
| find_host_connection called from main_inI1_outR1
| find_host_pair_conn (find_host_connection2): 192.168.1.2:500 %any:181 -> hp:no
ne
packet from 66.227.95.240:181: initial Main Mode message received on 192.168.1.2
:500 but no connection has been authorized
| complete state transition with STF_IGNORE
| next event EVENT_PENDING_PHASE2 in 98 seconds

```

Does anyone have any ideas how to get this working? Also, please correct any inaccuracies in what I've said. I've been reading a lot about this over the past few weeks and I don't want to perpetuate any misinformation. Thank you!

---

### Post by puppywhacker on 2008-11-04
Hi,

I used the package ipsec-tools, not openswan. I used the [http://www.ipsec-howto.org/](http://www.ipsec-howto.org/)

protocoltype 47 is for GRE tunnels, which is a different point-to-point tunnel, 50 and 51 are for IPsec, ESP is doing encryption, AH is for signing

/etc/protocols
gre     47      GRE             # General Routing Encapsulation
esp     50      IPSEC-ESP       # Encap Security Payload [RFC2406]
ah      51      IPSEC-AH        # Authentication Header [RFC2402]

SIP by default use port 5060 and the RTP port is assigned dynamically. I'm a bit confused though on why you forward the ports, with IPsec you can either tunnel between two IP addresses, or specify the ports. So forwarding SIP is pretty easy, but the RTP ports should then be limited to a small range.

And a technicallity, asterisk does not necessarily proxy a call, it is for locating the parties, but if a suitable codec can be negotiated between the two parties the RTP speech can go straight from phone to phone.

eitherway, goodluck

---

### Post by piusvelte on 2008-11-04
> **puppywhacker said:**
> Hi,

I used the package ipsec-tools, not openswan. I used the [http://www.ipsec-howto.org/](http://www.ipsec-howto.org/)

protocoltype 47 is for GRE tunnels, which is a different point-to-point tunnel, 50 and 51 are for IPsec, ESP is doing encryption, AH is for signing

/etc/protocols
gre     47      GRE             # General Routing Encapsulation
esp     50      IPSEC-ESP       # Encap Security Payload [RFC2406]
ah      51      IPSEC-AH        # Authentication Header [RFC2402]

Great info thank you! GRE sounds familiar and I'll try opening 51 also. I'll read up on ipsec-tools as an alternative. Did you have any problems with natt or with the vpn server being behind a router?

> **puppywhacker said:**
> 
I'm a bit confused though on why you forward the ports, with IPsec you can either tunnel between two IP addresses, or specify the ports. So forwarding SIP is pretty easy, but the RTP ports should then be limited to a small range.

And a technicallity, asterisk does not necessarily proxy a call, it is for locating the parties, but if a suitable codec can be negotiated between the two parties the RTP speech can go straight from phone to phone.


I had read that asterisk was different from standard pbx's as it takes an incoming call and becomes a client dialing out to the recipient, whereas sip normally allows two end points to talk directly with the pbx being only a locator as you describe. So this is incorrect? Also, either way, between dynamic ip and nat, asterisk can't locate the recipient, which is why I'm looking at vpn. 5060 won't be forwarded as it will hopefully be tunneled as you pointed out.

> **puppywhacker said:**
> eitherway, goodluck
Thank you! I'm off to [http://www.ipsec-howto.org/](http://www.ipsec-howto.org/) now!

---

### Post by piusvelte on 2008-11-04
Opening protocol 51 doesn't appear to have made a difference. I'm still reading through the how-to above.

---

### Post by puppywhacker on 2008-11-04
Hi,

I don't have problems with nat's, my server is not behind a nat, only some clients are. So I don't have any experience using STUN or ICE methods 

In the /etc/asterisk/sip.conf you can specify for each client that it requires a nat.
nat=yes

GRE is a plain IP over IP tunneling, IPsec is more advanced and will (optionally) encrypt the tunnel. But I don't think you need either for a server to be reachable behind a NAT you could forward port 5060 and see if your clients deal with NAT properly.

I recommend making tcpdump / wireshark traces to see how the clients behave, and look at the /var/log/asterisk/messages.log for clues or look at the asterisk console by running "asterisk -rvvvv"

And you are correct, asterisk can act as rtp-gateway when the end-points can't reach each other directly. This is called B2BUA back2back useragent. I don't think (hope) asterisk does this all the time though.

I know it's not the full answer, but I hope it points you in the right direcion.

goodluck

---

