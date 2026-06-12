---
title: "DSL shutting down - using pppoe"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by infoseeker on 2008-01-18
I have been using my Netgear DG834 in bridge mode to connect to the internet for the past few years and have not had any problems, until this week.

I setup my connection using 'pppoeconf' and always connect on reboot without any problems, and using 'pon dsl-provider' otherwise.

What is happening now is the connection drops (randomly?) and I am unable to use the net.  'ifconfig' lists no connection for ppp0 as it normally would.  I cannot browse the Netgear on 192.168.0.1, or even ping it, so my network seems to be affected too (firewall maybe, but firestarter tells me that the firewall is down as there is no ppp0 connection).

If I do a 'poff' the response seems positive, but if I then attempt a 'pon dsl-provider' (which I have been using for years), I cannot connect.
```
Jan 18 22:23:03 --- pppd[8865]: Plugin rp-pppoe.so loaded.
Jan 18 22:23:03 --- pppd[8867]: pppd 2.4.4 started by root, uid 0
Jan 18 22:23:39 --- pppd[8867]: Timeout waiting for PADO packets
```

```
# Minimalistic default options file for DSL/PPPoE connections
noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth0
usepeerdns
user "xxxxxxxxxxxx@xxxxxxxxxxxxx"

```

As soon as conky reports my internet ip address as '0.0.0.0' I know I am disconnected, and I reboot to reconnect :(

Anybody able to help me ?

EDIT This is not worth bumping so I am editing it directly, as this problem has cleared up completely (for now?).  I moved my network card to another PCI slot and has been stable since (close to 24 hrs).:confused:

---

