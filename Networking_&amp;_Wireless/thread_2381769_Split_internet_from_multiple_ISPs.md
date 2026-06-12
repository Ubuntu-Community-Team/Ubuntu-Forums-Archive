---
title: "Split internet from multiple ISPs"
date: 2018-01-05
forum: Networking &amp; Wireless
---

### Post by QuimNuss on 2018-01-05
Our setting is as follows:
```

                                                                      
                                        +---------+    +------------+        /
                                        |         |    |  Modem     |       /
                     +-----------+------| Firewall|----+ Provider 1 +-------
            __       |           |      |         |    |            |    /
        ___/  \_     |    +------+----+ +---------+    +------------+   |
      _/        \__  |    |     p4p1  |                               /
     /             \ |    |           |                              |
    | Local network -+    |Ubuntu srv |                              |Internet
     \_           __/     |           |                              |
       \__     __/        |     em1   |                               \
          \___/           +------+----+     +------------+             |
                                 |          |  Router    |              \
                                 +----------+ Provider 2 +----------------
                                            |            |                |
                                            +------------+         


```

We would like the Ubuntu server to be able to use the `em1` interface, specially for ftp traffic. 

That makes it harder, I believe, since FTP creates connections on Passive Mode that should be correctly routed through the `em1`. Am I mistaken to raise a red flag here?

We don't need nor want load balancing, and the LAN won't access the Internet through `em1`, so that should make things easier since the Ubuntu server doesn't have to reroute anything coming from `em1`.

We have a static public address given to the firewall, but the router of Provider 2 will have a dynamic address that we will have to DynDNS or something.

I've found this [HOWTO]([http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)) and [this stackoverflow question]([https://serverfault.com/questions/392183/load-balancing-isps-on-ubuntu-server](https://serverfault.com/questions/392183/load-balancing-isps-on-ubuntu-server)) but I'm confused on that script values.

What are the IP1 and IP2 values really? Which will be the default route for packets originating from the ubuntu server? Where is that default route set and to which value? Is the P0_NET unnecessary in my case?

How would I modify that script to fit my case scenario? I believe it should _at least_ be 

```

    #!/bin/bash -v
    #IPs of device connected to the internet
    IP1=192.168.30.240 (or is it the public ip 85.12.34.56?)
    #static IP provided by ISP2
    IP2=192.168.0.10 (or is it the dynamic ip 190.12.34.56?)
    
    #Your Gateways (type route in terminal it should be in the same line as default)
    P1=192.168.30.1 #gateway provided by ISP1
    P2=192.168.0.254 #gateway provided by ISP2
    
    #Your Subnets
    P1_NET=192.168.0.0/24 #local network subnet + p4p1
    P2_NET=192.168.10.0/24 #em1 LAN
    # NICs your internet interfaces
    IF1=p4p1
    IF2=em1
    
    ip route add $P1_NET dev $IF1 src $IP1 table T1
    ip route add default via $P1 table T1
    ip route add $P2_NET dev $IF2 src $IP2 table T2
    ip route add default via $P2 table T2
    ip route add $P1_NET dev $IF1 src $IP1
    ip route add $P2_NET dev $IF2 src $IP2
    
    ip rule add from $IP1 table T1
    ip rule add from $IP2 table T2
    ip route add $P2_NET dev $IF2 table T1
    ip route add 127.0.0.0/8 dev lo table T1
    ip route add $P1_NET dev $IF1 table T2
    ip route add 127.0.0.0/8 dev lo table T2

```

---

