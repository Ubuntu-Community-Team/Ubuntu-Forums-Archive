---
title: "Networking basics: The ip addr show command interpretation?"
date: 2014-04-26
forum: Networking &amp; Wireless
---

### Post by minoo_toxic on 2014-04-26
Hi all,
I'm new to Linux and I have a question regarding this network command:
What's the interpretation of the result of ip addr show command for an interface:

 eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether --------------------------
    inet---------------------------- scope global eth1
       valid_lft forever preferred_lft forever
    inet6 --------------------------- scope link 
       valid_lft forever preferred_lft forever

I know the second line is the MAC address and line 3 and 4 are the information about IPv4 and IPv6 respectively but I'm not sure what do the first and last line exactly means?!
I just know that UP means that the interface in up and running but what about the broadcast, multicast and lower up flags?
some elaboration on the other keywords of this result would be appreciated. 

Thanks in advance for your help. :)

---

### Post by ian-weisser on 2014-04-27
I think it's really well explained in the ifconfig manual page
```
man ifconfig
```

---

