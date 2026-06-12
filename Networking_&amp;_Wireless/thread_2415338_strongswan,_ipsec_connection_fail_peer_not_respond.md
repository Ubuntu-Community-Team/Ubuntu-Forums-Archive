---
title: "strongswan, ipsec connection fail: peer not responding"
date: 2019-03-24
forum: Networking &amp; Wireless
---

### Post by adrhc on 2019-03-24
Hi, using *Ubuntu 16.04.6 LTS* (4.4.0-67-generic, x86_64) I'm trying to create an *ipsec* connection with this configuration:

**/etc/ipsec.conf**
```
conn %default
    ikelifetime=60m
    keylife=20m
    rekeymargin=3m
    keyingtries=1
    keyexchange=ikev1
#    authby=secret
    authby=psk
#    ike=aes256-md5-modp1024,3des-sha1-modp1024!
    # esp=aes256-md5-modp1024,3des-sha1-modp1024!
conn CETTOV
#    keyexchange=ikev1
    left=%defaultroute
#    left=172.20.19.7
    auto=add
#    authby=secret
#    type=transport
#    leftprotoport=17/1701
#    rightprotoport=17/1701
    # set this to the ip address of your vpn server
    right=214.178.16.197
#    rightsubnet=213.177.15.0/24
    leftfirewall=yes

```

**/etc/ipsec.secrets**
```
: PSK "some secret"
```

**/etc/xl2tpd/xl2tpd.conf**
```
[lac CETTOV]
lns = 214.178.16.197
ppp debug = yes
pppoptfile = /etc/ppp/options.l2tpd.client
length bit = yes

```

**/etc/ppp/options.l2tpd.client**
```
ipcp-accept-local
ipcp-accept-remote
refuse-eap
require-mschap-v2
noccp
noauth
idle 1800
mtu 1410
mru 1410
defaultroute
usepeerdns
debug
lock
connect-delay 5000

```

and I get:

```
initiating Main Mode IKE_SA CETTOV[1] to 214.178.16.197
generating ID_PROT request 0 [ SA V V V V ]
sending packet: from 172.20.19.7[500] to 214.178.16.197[500] (248 bytes)
received packet: from 214.178.16.197[500] to 172.20.19.7[500] (156 bytes)
parsed ID_PROT response 0 [ SA V V V V ]
received NAT-T (RFC 3947) vendor ID
received DPD vendor ID
received XAuth vendor ID
received unknown vendor ID: 82:99:03:17:57:a3:60:82:c6:a6:21:de:00:05:02:e0
generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
sending packet: from 172.20.19.7[500] to 214.178.16.197[500] (372 bytes)
received packet: from 214.178.16.197[500] to 172.20.19.7[500] (356 bytes)
parsed ID_PROT response 0 [ KE No NAT-D NAT-D ]
local host is behind NAT, sending keep alives
generating ID_PROT request 0 [ ID HASH N(INITIAL_CONTACT) ]
sending packet: from 172.20.19.7[4500] to 214.178.16.197[4500] (108 bytes)
sending retransmit 1 of request message ID 0, seq 3
sending packet: from 172.20.19.7[4500] to 214.178.16.197[4500] (108 bytes)
sending retransmit 2 of request message ID 0, seq 3
sending packet: from 172.20.19.7[4500] to 214.178.16.197[4500] (108 bytes)
sending retransmit 3 of request message ID 0, seq 3
sending packet: from 172.20.19.7[4500] to 214.178.16.197[4500] (108 bytes)
sending keep alive to 214.178.16.197[4500]
sending retransmit 4 of request message ID 0, seq 3
sending packet: from 172.20.19.7[4500] to 214.178.16.197[4500] (108 bytes)
sending keep alive to 214.178.16.197[4500]
sending keep alive to 214.178.16.197[4500]
sending retransmit 5 of request message ID 0, seq 3
sending packet: from 172.20.19.7[4500] to 214.178.16.197[4500] (108 bytes)
sending keep alive to 214.178.16.197[4500]
sending keep alive to 214.178.16.197[4500]
sending keep alive to 214.178.16.197[4500]
giving up after 5 retransmits
establishing IKE_SA failed, peer not responding
establishing connection 'CETTOV' failed

```

214.178.16.197 is having full access to my computer through my firewall.

What is the problem? How can I solve it?

---

