---
title: "shared Internet too slow using iptables"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by lucifercheff on 2006-10-16
I'm running kubuntu dapper on a PIII 448SDRAM machine which i use as a router frontier for my home network. The problem is that the internet connection from inside network is too slow, almost non-existent. I can ping the two computers on the private network, so the LAN is ok. The Internet connection also works. I ran the following script to share the connection:

```

#!/bin/bash




iptables -F
iptables -X
iptables -Z
iptables -t nat -F


iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT


iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

echo 1 > /proc/sys/net/ipv4/ip_forward


iptables -A FORWARD -i ra0 -o eth0 -j ACCEPT

iptables -A FORWARD -i eth0 -o ra0 -m state --state RELATED,ESTABLISHED -j ACCEPT

``` 

Firestarter doesn't work either and I have disabled ipv6. It's not a DNS issue because i was browsing using ip instead of names.

Can anybody help me?

---

### Post by Woei on 2006-10-16
I'm surprised it's working at all. You're not letting ***new*** connections, originating from the LAN in your FORWARD chain through. Replace the last two rules with something more like this:
```

iptables -A FORWARD -i eth0 -o ra0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ra0 -o eth0 -j ACCEPT -m state --state ESTABLISHED, RELATED -j ACCEPT

```

Moreover, in the NAT table on the POSTROUTING chain, shouldn't the output interface be ra0 instead of eth0 ?

---

### Post by lucifercheff on 2006-10-16
Sorry, I forgot to indicate it:

eth0: Interface which is connected to my cablemodem.

ra0: Wireless LAN interface.  

Thanks anyway.

---

### Post by lucifercheff on 2006-10-18
nobody knows what's wrong?

---

### Post by mips on 2006-10-18
I was going to suggest Firestarter but then I saw you said it does not work. Why does it not work ?

whats the output ofthe following on the router & a pc:
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig -a
route -n

Disable IPv6 globally on all pc's.
Configure your ISPs DNS ip addresses manually on all machines (I know you said it's not a dns issue but just try it as dns might work but could slow things down)

---

