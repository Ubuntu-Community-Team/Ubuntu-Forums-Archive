---
title: "Reply on same interface from which the request came?"
date: 2024-02-17
forum: Networking &amp; Wireless
---

### Post by autominus on 2024-02-17
I have 2 network interfaces in my virtual machine. Both interfaces  should have a default gateway. One interface is connected to the  Intranet. The second is connected to the Internet.
 ```
                                      Host
              +---------+      +----------------+
Intranet <--> | Gateway | <--> |     ens001     |
              +---------+      |  10.20.50.100  |
                               |----------------|
                               |     ens104     |      +---------+        
                               |  10.25.40.200  | <--> | Gateway | <--> Internet
                               +----------------+      +---------+ 
```
 My connection doesn't work properly and outgoing traffic always goes through one interface (ens104). My routing table:
 ```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    100    0        0 ens104
default         _gateway        0.0.0.0         UG    100    0        0 ens001
10.20.50.0      0.0.0.0         255.255.252.0   U     100    0        0 ens001
_gateway        0.0.0.0         255.255.255.255 UH    100    0        0 ens001
10.25.40.0      0.0.0.0         255.255.255.0   U     100    0        0 ens104
_gateway        0.0.0.0         255.255.255.255 UH    100    0        0 ens104

``` How can I get the Linux TCP/IP stack to answer back on the same interface as a request came from.

---

### Post by TheFu on 2024-02-17
The only way to control which interface gets traffic is through the routing table.  The one above has 2 default routes, which makes no sense if they are truly **intra**net and **inter**net.  Also, use the metrics to control which has priority, so make the LAN subnet lower than 100.

The direct routes to _gateway aren't helping or needed.

We need to know which OS release you are running to provide any more help, since the networking configuration subsystem has changed drastically in the last 10 yrs, with major changes happening with each LTS release.

---

### Post by autominus on 2024-02-18
I use Ubuntu 22.04.3 LTS. Please help me solve my problem.

---

### Post by TheFu on 2024-02-18
> **autominus said:**
> I use Ubuntu 22.04.3 LTS. Please help me solve my problem.

Server or desktop?  Any DE?  22.04 is too new for me. Perhaps someone else can help with the netplan settings.  netplan is documented at [http://netplan.io](http://netplan.io)

---

### Post by autominus on 2024-02-18
I use Ubuntu **Server** 22.04.3 LTS.

---

### Post by TheFu on 2024-02-18
> **autominus said:**
> I use Ubuntu **Server** 22.04.3 LTS.

For anyone to help, you'll need to post the contents of the current netplan file(s) and they **must** be wrapped in forum code tags, since netplan uses YAML and YAML is space sensitive.

---

### Post by autominus on 2024-02-18
netplan YAML file:
```

# This is the network config written by 'subiquity'
network:
  ethernets:
    ens001:
      dhcp4: true
#      dhcp4-overrides:
#        route-metric: 10
      routes:
      - to: default
        via: 10.222.55.254
        table: 1
        metric: 10
      routing-policy:
      - from: 10.222.52.250
        table: 1
    ens104:
      dhcp4: true
#      dhcp4-overrides:
#        route-metric: 20
      routes:
      - to: default
        via: 10.250.4.254
        table: 2
        metric: 20
  version: 2

```

When I use  "dhcp4-overrides: route-metric: 10", the network stops working on both interfaces.

My routing table:
```

debs@uni:~$:/etc/netplan$ sudo ip route list table 1
default via 10.20.50.254 dev ens001 proto static metric 10 onlink

debs@uni:~$:/etc/netplan$ sudo ip route list table 2
default via 10.25.40.254 dev ens104 proto static metric 20 onlink

debs@uni:~$:/etc/netplan$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.25.40.254    0.0.0.0         UG    100    0        0 ens104
0.0.0.0         10.20.50.254    0.0.0.0         UG    100    0        0 ens001
10.20.50.0      0.0.0.0         255.255.255.0   U     100    0        0 ens001
10.20.50.254    0.0.0.0         255.255.255.255 UH    100    0        0 ens001
10.25.40.0      0.0.0.0         255.255.255.0   U     100    0        0 ens104
10.25.40.254    0.0.0.0         255.255.255.255 UH    100    0        0 ens104

```

---

### Post by TheFu on 2024-02-18
Don't use DHCP. That's step 1.  
Don't setup 1 default routes. That's step 2.  The non-internet route needs to be for all the LAN subnets you want to access.

---

