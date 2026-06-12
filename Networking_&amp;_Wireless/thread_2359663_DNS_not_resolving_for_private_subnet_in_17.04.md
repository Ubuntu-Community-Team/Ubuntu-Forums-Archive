---
title: "DNS not resolving for private subnet in 17.04"
date: 2017-04-26
forum: Networking &amp; Wireless
---

### Post by twoj on 2017-04-26
Hello
I'm running into a dead end here.  I'm trying to configure Ubuntu 16.04 with a private subnet.  I have 2 NICs;  One is for WAN (DHCP assigned address) the other for the LAN local/private subnet.
I have followed instructions for 16.04: [https://killtacknine.com/building-an-ubuntu-16-04-router-part-1-network-interfaces/](https://killtacknine.com/building-an-ubuntu-16-04-router-part-1-network-interfaces/)
Here is what is what I'm seeing:
1) Private subnet PC is being assigned dynamic IP address.
2) Private subnet PC does not resolve DNS names nor I can ping any of the global IP addresses from it.
3) Private subnet PC can access the LAN nic via ping.
4) I have added a route in ubuntu so that WAN subnet can see LAN subnet allow me to ping WAN nic directly from from the private subnet.
5) Ubuntu 16.04 has internet access and a working DNS resolution.

So my problem seems to be that the traffic from the private subnet is not resolved correctly in Ubuntu and not routed to the WAN nic?!?!  

Any suggestions are appreciated.

Regards

---

### Post by Doug S on 2017-04-26
Please post your bind9 configuration files. In addition to the reference you are using, look at [the Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/dns.html").

---

### Post by twoj on 2017-04-26
Here they are:

/etc/bind/named.conf
```

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

```


/etc/bind/named.conf.options
```

options {
    directory "/var/cache/bind";


        recursion yes;

    forwarders {
       8.8.8.8;
           8.8.4.4;
    };


    dnssec-validation auto;


    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};

```


/etc/bind/named.conf.default-zones
```

// prime the server with knowledge of the root servers
zone "." {
    type hint;
    file "/etc/bind/db.root";
};


// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912


zone "localhost" {
    type master;
    file "/etc/bind/db.local";
};


zone "127.in-addr.arpa" {
    type master;
    file "/etc/bind/db.127";
};


zone "0.in-addr.arpa" {
    type master;
    file "/etc/bind/db.0";
};


zone "255.in-addr.arpa" {
    type master;
    file "/etc/bind/db.255";
};

```


/etc/bind/db.local
```

;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    localhost. root.localhost. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    localhost.
@    IN    A    127.0.0.1
@    IN    AAAA    ::1

```


enp1s0f0 = WAN NIC
enp1s0f1 = LAN Private Subnet NIC

ifconfig
```

enp1s0f0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.102  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 2601:18a:c404:78a0:a236:9fff:febc:c05c  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::a236:9fff:febc:c05c  prefixlen 64  scopeid 0x20<link>
        ether a0:36:9f:bc:c0:5c  txqueuelen 1000  (Ethernet)
        RX packets 1960  bytes 362386 (362.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2483  bytes 1789919 (1.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp1s0f1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.2  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a236:9fff:febc:c05e  prefixlen 64  scopeid 0x20<link>
        ether a0:36:9f:bc:c0:5e  txqueuelen 1000  (Ethernet)
        RX packets 477  bytes 95209 (95.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 200  bytes 24869 (24.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether f4:8e:38:9a:f5:42  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 422  bytes 33247 (33.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 422  bytes 33247 (33.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```


finally:

nmcli dev show enp1s0f0 
```

GENERAL.DEVICE:                         enp1s0f0
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         A0:36:9F:BC:C0:5C
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         10.0.0.102/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.ADDRESS[1]:                         2601:18a:c404:78a0:a236:9fff:febc:c05c/64
IP6.ADDRESS[2]:                         fe80::a236:9fff:febc:c05c/64
IP6.GATEWAY:                            fe80::68ee:96ff:feb1:2810

```


nmcli dev show enp1s0f1
```

GENERAL.DEVICE:                         enp1s0f1
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         A0:36:9F:BC:C0:5E
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.2/24
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         fe80::a236:9fff:febc:c05e/64
IP6.GATEWAY:                            

```

cat /run/resolvconf/resolv.conf
```

nameserver 75.75.75.75
nameserver 75.75.75.74
nameserver 127.0.0.1


search xxx.xx.comcast.net

```


One more clue:  I have set up port forwarding through Ubuntu and it work fine. 

Please help!

---

### Post by twoj on 2017-04-29
The other thing that I'm seeing is that when I do:

```

dig @127.0.0.1 google.com

```

the dns DOES NOT work.

but:

```

dig google.com

```

Works just fine.   So the problem has to be in the routing?!?

THanks

---

