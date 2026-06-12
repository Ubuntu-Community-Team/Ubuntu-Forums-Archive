---
title: "Keepalived and unable to route to any IP addresses on the backup"
date: 2018-02-16
forum: Networking &amp; Wireless
---

### Post by Andrew_Welham on 2018-02-16
Not sure if this is normal behaviour
I have the following multiple configs like the examples below for multiple NICs
 on subnets 192.168.0.0/24 192.168.1.0/24 etc
Master Server
```

vrrp_instance Servers {
    state MASTER
    interface enp0s10
    virtual_router_id 50
    priority 100
    advert_int 1
    authentication {
        auth_type PASS
        auth_pass PASSWORD
    }
    unicast_peer {
    192.168.0.3
    }
    virtual_ipaddress {
    192.168.0.1
    }
}

```
backup server


```

vrrp_instance Servers {
    state BACKUP
    interface enp0s10
    virtual_router_id 50
    priority 99
    advert_int 1
    authentication {
        auth_type PASS
        auth_pass PASSWORD
    }
    unicast_peer {
    192.168.0.2
    }
    virtual_ipaddress {
    192.168.0.1
    }
}

```



In this case i client on network 192.168.0.0/24 can always see 192.168.0.1 , 192.168.0.2 & 192.168.0.3

but can only see 192.168.1.1 and 192.168.1.2 if the master is active and 192.168.1.1 & 192.168.1.3 if the backup is active

Is almost like to two servers running keepalived are refusing to route to those each other.
However the servers are routing to other devices on the network.

Any ideas how to resolve ? As i need to access other servers on these two servers and not though the vip

Many Thanks

---

### Post by Andrew_Welham on 2018-02-16
It looks to do with arp cache as they were all empty, on the machine i was trying to ping (192.168.0.3) i'm getting

```

20:09:17.432869 ARP, Request who-has 192.168.1.1 tell 192.168.1.4, length 46
20:09:18.951236 IP 192.168.1.4 > 192.168.0.3: ICMP echo request, id 1, seq 315, length 40
20:09:23.948878 IP 192.168.1.4 > 192.168.0.3: ICMP echo request, id 1, seq 316, length 40
20:09:27.529015 ARP, Request who-has 192.168.1.1 tell 192.168.1.4, length 46
20:09:28.958330 IP 192.168.1.4 > 192.168.0.3: ICMP echo request, id 1, seq 317, length 40
20:09:33.954588 IP 192.168.1.4 > 192.168.0.3: ICMP echo request, id 1, seq 318, length 40
20:09:37.685258 ARP, Request who-has 192.168.1.1 tell 192.168.1.4, length 46
20:09:38.949913 IP 192.168.1.4 > 192.168.0.3: ICMP echo request, id 1, seq 319, length 40
20:09:43.938430 IP 192.168.1.4 > 192.168.0.3: ICMP echo request, id 1, seq 320, length 40
20:09:47.716826 ARP, Request who-has 192.168.1.1 tell 192.168.1.4, length 46

```


the client is 192.168.1.4
so the message is getting there but the reply is never leaving. I have manually set the arp cache to the correct nic and mac but still nothing

any ideas?

---

