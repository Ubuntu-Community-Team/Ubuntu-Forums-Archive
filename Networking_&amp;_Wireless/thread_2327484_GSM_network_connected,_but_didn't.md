---
title: "GSM network connected, but didn't"
date: 2016-06-11
forum: Networking &amp; Wireless
---

### Post by petyabest on 2016-06-11
Hi,

I have an Alcatel OneTouch X602D mobile broadband modem and an Ubuntu 14.04.

I can connect with the modem to the GSM network - seemingly.
The modem and the Ubuntu also seeing that the connection successfully established, however - in the most of cases - I couldn't use this connection.
(When I trying to ping an address, like 8.8.8.8, I got the message 'Network is unreachable.')

I realized that when I connected to the network, the routing table - in the most of cases - wrong.

In the most of cases the following routing table created:
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
91.104.127.35   *               255.255.255.255 UH    750    0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 ppp0


In this case the internet connectivity seems like established, but it is unreachable.

However some times its works, and routing table generated with right entries:
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         *               0.0.0.0         U     750    0        0 ppp0
netacc-gpn-204- *               255.255.255.255 UH    750    0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 ppp0


In this case the connection can be used and works perfectly.

How can I make the RIGHT routing table being created permanently, when I want to use my mobile connection?
(I using WiFi and Wired connections also, so I need to change between connections.)

---

