---
title: "special SNAT and DNAT gateway"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by pdaures on 2008-11-13
Hello,
I would like to create a gateway in order to do a special kind of NAT.
I need to do SNAT and DNAT in this way :

SNAT :
@src A.X.Y.Z -> A+1.X.Y.Z
Example:
@src 192.168.0.1 -> 193.168.9.1
@src 191.23.33 -> 192.23.33

DNAT :
@dst A.X.Y.Z -> A+1.X.Y.Z
Example:
@dst 168.1.0.1 -> 169.1.0.1
@dst 154.9.2.36> 155.9.2.36

I know how to do it with "static list" of @IP with iptables :
DNAT :
iptables -t nat -A PREROUTING -d 192.168.0.1  -j DNAT --to-destination
 193.168.0.1
SNAT
iptables -t nat -A POSTOUTING -s 168.1.0.1  -j DNAT --to-destination  169.1.0.1

But, as I have a large number of @IP, how can I do it for ALL ip addresses ?

Thank you for giving few secondes to explain me how to do it if you
have an answer.
Thank you !

---

