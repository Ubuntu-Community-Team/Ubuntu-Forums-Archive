---
title: "iptables - Route to the Internet"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by rogirwin on 2008-04-27
This is a firewall script that I written for my router. What I want to is allow traffic from LAN2 to access the internet but not anything else on the network. I have set "INTERNET" to 0.0.0.0/32 and it forwards traffic ok but it also allows it to see everything else on LAN1. There is a static route between the two LANs.

What should "INTERNET" be set to?

```
# Set variabes
IPT="/usr/sbin/iptables"
LAN1="192.168.1.0/24"
LAN2="10.1.1.0/24"
INTERNET="x.x.x.x/x"

# Flush the chains
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD
$IPT -F -t nat

# Set the policys
$IPT -P FORWARD DROP
$IPT -P INPUT ACCEPT
$IPT -P OUTPUT ACCEPT

$IPT -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT

$IPT -A FORWARD -s $LAN2 -d $INTERNET -j ACCEPT
```

---

### Post by helgman on 2008-04-27
I've not had that much experience with IP-tables, but I've written my fair share of access controll lists. My guess is that your last line says that anything comming from LAN2 can go anywhere, includning LAN1.

Perhaps you should have a line above it making it into something like this:
```
$IPT -A FORWARD -s $LAN2 -d $LAN1 -j DROP
$IPT -A FORWARD -s $LAN2 -d $INTERNET -j ACCEPT
```

I've not tested it but my guess is that when a packet from LAN2 tries to access LAN1 the first line will trigger and drop the package. In any other case the package will fly.

Maybe?

// Helgman

---

### Post by rogirwin on 2008-04-27
> **helgman said:**
> 
```
$IPT -A FORWARD -s $LAN2 -d $LAN1 -j DROP
$IPT -A FORWARD -s $LAN2 -d $INTERNET -j ACCEPT
```
// Helgman

Yes, That would work as long as you put the DROP line second. Allowing 0.0.0.0/32 is basically like saying "everything".

The reason I don't want to do it that was is that if I end up adding LAN3 or LAN4 somewhere down the track I will have to adjust the script. If I forget to I then have a security hole in my network.

Is there a way to distinguish between LAN traffic and WAN traffic?

---

### Post by helgman on 2008-04-27
> **rogirwin said:**
> Is there a way to distinguish between LAN traffic and WAN traffic?

Destination and/or source address depending on direction.

You could write rules that denies all addresses that RFC 1918 defines as "private", that is 10.0.0.0/8, 172.16.0.0/12 and 192.168.0.0/16. this should work, as long as you don't use public addresses on any LAN you add ...

Regards,
Helgman

---

