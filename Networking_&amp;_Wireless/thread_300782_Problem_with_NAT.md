---
title: "Problem with NAT"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Frunktz on 2006-11-16
Hi!
Weird problem.

SERVER (Kubuntu 6.10)
- eth0 -> LAN
- eth1 -> linked to ethernet modem (ppp0)
- ath0 -> WIFI

CLIENT (Kubuntu 6.10)
- eth0 -> LAN
- ath0 -> WIFI

I want to allow client to connect to internet throught SERVER.
Obvius I search in the forum regard iptables, nat, masquerading, ip_forward.
I try some script but the weird problem is: client can ping any pc on the net, but he can connect only to google.com (I cannot apt-get update or navigate in ubuntuforums). If I try to connect from server the connection is perfect.

I try various script, one of them is that.
```

# enable ip forwarding in the kernel
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward
                                                                               
# flush rules and delete chains
$IPTABLES -F
$IPTABLES -X
                                                                               
# enable masquerading to allow LAN internet access
$IPTABLES -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
                                                                               
# forward LAN traffic from eth0 to Internet interface ppp0
$IPTABLES -A FORWARD -i eth0 -o ppp0 -m state --state NEW,ESTABLISHED -j ACCEPT

```

Why I can't connect normally? Ps:- No firewall in both pc

---

