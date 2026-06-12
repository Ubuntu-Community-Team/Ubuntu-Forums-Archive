---
title: "Does Ubuntu Desktop have dual IPv4 and IPv6 stack?"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by TonyUb on 2008-08-04
Folks,

ISPs over my way are starting to provide IPv6 (e.g. [http://ipv6.internode.on.net/](http://ipv6.internode.on.net/)) on their networks. Windows Vista has a dual IPv4/IPv6 stack.

Just wondering if Ubuntu has a similar way of doing things?

Regards

Tony

---

### Post by cariboo on 2008-08-05
The short answer is yes. To see that ipv6 is enable in a terminal tyoe:

```
cat /etc/hosts
```

you should see something like this:

```
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

and in a terminal:

```
ifconfig
```

resulting in:

```
eth0      Link encap:Ethernet  HWaddr 00:16:17:9c:84:b5  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe9c:84b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2533301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2602888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2168547669 (2.1 GB)  TX bytes:993080586 (993.0 MB)
          Interrupt:20 Base address:0xe000
```

Note the inet6 addr:

Jim

---

### Post by TonyUb on 2008-08-05
Interesting.

Say I didn't want to use DHCP and want to give a Ubuntu Desktop box a "fixed" IP address of 192.168.0.11 under IPv4 could you please advise how I can give the Ubuntu Desktop box also an IPv6 "fixed" IP address as well?

Also, if I wanted to use just one stack is there a way of disabling the other? Please advise.

Finally, I gather that IPv6 has additional security provisions (e.g. encryption?) is this enabled by default?

Regards,

Tony

---

