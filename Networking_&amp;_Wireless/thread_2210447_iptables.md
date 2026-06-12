---
title: "iptables"
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by sylvain2 on 2014-03-10
Hi all,

I am having a problem with iptables. when I input these rule I am unable to ping anything anymore and unable to nslookup?
 iptables -A INPUT -j DROP
iptables -I INPUT 1 -i eth0 -s 99.99.128.180 -p tcp --dport 2014 -j ACCEPT

Thanks for helping me

---

### Post by tomearp on 2014-03-11
Anything that is not coming from 99.99.128.180 to port 2014 of the machine is being dropped. This includes all ICMP echo replies, DNS lookup replies and so on.

Something like the following may be better:
```
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -s 99.99.128.180 -p tcp --dport 2014 -j ACCEPT
iptables -A INPUT -j DROP
```

The connection tracking module will recognise incoming traffic such as ICMP echo replies etc. and will allow them through.
FYI, if you change the default policy for the INPUT table to DROP (iptables -P INPUT DROP) then you don't need to add the third rule as anything that reaches the end will be automatically dropped.

---

