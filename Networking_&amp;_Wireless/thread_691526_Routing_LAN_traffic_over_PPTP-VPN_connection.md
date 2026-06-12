---
title: "Routing LAN traffic over PPTP-VPN connection"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by awarberg on 2008-02-08
Hi

I succesfully setup a PPTP VPN connection to a Microsoft box by following [http://pptpclient.sourceforge.net/howto-ubuntu.phtml#configure_by_hand](http://pptpclient.sourceforge.net/howto-ubuntu.phtml#configure_by_hand) and for routing this guide: [http://pptpclient.sourceforge.net/routing.phtml#automatic-setup](http://pptpclient.sourceforge.net/routing.phtml#automatic-setup)

I can ping hosts on the remove lan from the machine, which establish the connection.

I would like to allow traffic from the local lan to pass through the connected machine to the remote lan.

On my Windows machine I tried to add a route like this:
route add 10.45.1.0 mask 255.255.255.0 192.168.0.197

where 10.45.1.0 is the remote lan and 192.168.0.197 is the gateway with an established VPN connection.

But I cannot ping hosts in the 10.45.1.0 network!

The routing table on my windows machine goes like this:
Aktive ruter:
Netværksdestination        Netmaske          Gateway       Grænseflade  Metrikværdi
          0.0.0.0          0.0.0.0      192.168.0.1   192.168.0.198       25
**        10.45.1.0    255.255.255.0    192.168.0.197   192.168.0.198       1**
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.0.0    255.255.255.0    192.168.0.198   192.168.0.198       25
    192.168.0.198  255.255.255.255        127.0.0.1       127.0.0.1       25
    192.168.0.255  255.255.255.255    192.168.0.198   192.168.0.198       25
        224.0.0.0        240.0.0.0    192.168.0.198   192.168.0.198       25
  255.255.255.255  255.255.255.255    192.168.0.198               2       1
  255.255.255.255  255.255.255.255    192.168.0.198   192.168.0.198       1
Standardgateway:       192.168.0.1

The line in bold should give me a route to the remote lan.

Maybe I need to configure some routing on 192.168.0.197? It is an ubuntu 7.10 server and the routing script, which is with the vpn connection, goes like this:

[PHP]#!/bin/sh

if [ "${PPP_IPPARAM}" = "mytunnel" ]; then

   route add -net 10.45.1.0/24 dev ${IFNAME}

iptables --insert OUTPUT 1 \
   --source 0.0.0.0/0.0.0.0 \
   --destination 10.45.1.0/24 \
   --jump ACCEPT --out-interface ${IFNAME}

iptables --insert INPUT 1 \
   --source 10.45.1.0/24 \
   --destination 0.0.0.0/0.0.0.0 \
   --jump ACCEPT --in-interface ${IFNAME}

iptables --insert FORWARD 1 \
   --source 0.0.0.0/0.0.0.0 \
   --destination 10.45.1.0/24 \
   --jump ACCEPT --out-interface ${IFNAME}

iptables --insert FORWARD 1 \
   --source 10.45.1.0/24 \
   --destination 0.0.0.0/0.0.0.0 --jump ACCEPT

iptables --table nat --append POSTROUTING \
   --out-interface ppp0 --jump MASQUERADE

iptables --append FORWARD --protocol tcp --tcp-flags SYN,RST SYN \
   --jump TCPMSS --clamp-mss-to-pmtu

fi[/PHP]

I hope you can help me.

Best regards
Andreas

---

### Post by cmnorton on 2008-02-09
pptpconfig gives you the opportunity to denote a subnet on one of the configuration screens. Providing your remote subnet, like 10.100.0/16, should allow you to ping/reach your hosts on the remote site of the VPN.

Unfortunately, I'm using Network Manager now, otherwise I'd point you to the exact place.

---

### Post by awarberg on 2008-02-09
Hi cmnorton

Thanks. This is working already and the vpn client machine can reach machines on the remote lan. Now, in addition, I want to route traffic from any host on the local lan, through the vpn client host, to the remote lan.

Kind regards,
Andreas

---

### Post by cmnorton on 2008-02-11
To the best of my memory, one of the tabs in pptpconfig allows you to specify stuff like routing your traffic through the vpn. You can also go look in the config files pptp configu uses. I'd look under /etc/ppp, and search these forums for many posts on pptpconfig.

---

### Post by awarberg on 2008-02-11
Okay thanks. I prefer to setup this up without pptpconfig and I'm sure its just a matter of a few iptables instructions ala those used for setting Linux up as an internet gateway.

---

### Post by The Cog on 2008-02-11
You always also need to worry about the return path - packets from the work LAN to your home network. Since your home network is almost certainly not being advertised in the routing tables at work, you probably need to do masquerading on your VPN interface to make the other home machines look like your PC.

And you need to enable IP forwarding of course. To enable IP forwarding, add this line to /etc/sysctl.conf:
```
net.ipv4.ip_forward=1
```

---

