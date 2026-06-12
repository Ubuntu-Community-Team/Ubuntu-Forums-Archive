---
title: "[Ubuntu 20.04] No request thru the second NIC on an AWS EC2"
date: 2020-12-28
forum: Networking &amp; Wireless
---

### Post by fred2mtl on 2020-12-28
Hi,

I want to have an EC2 instance, running Ubuntu 20.04, hosted into a private subnet and having a second NIC (named ens6) tied to a public subnet. The configuration with netplan works fine, showing the ENI is up on the EC2, as following:

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens5: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc mq state UP group default qlen 1000
    link/ether 0e:60:f2:f7:63:60 brd ff:ff:ff:ff:ff:ff
    inet xx.xx.xx.xx/22 brd xx.xx.xx.xx scope global dynamic ens5
       valid_lft 3239sec preferred_lft 3239sec
    ...
3: ens6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 0e:6f:66:be:57:60 brd ff:ff:ff:ff:ff:ff
    inet xx.xx.xx.xx/22 brd xx.xx.xx.xx scope global ens6
       valid_lft forever preferred_lft forever
    ...

```

My tools (postfix, dovecot, etc) listens on all networks, but are never reached by a request coming thru ens6. What have I missed, please?

Thanks in advance

Fred

---

