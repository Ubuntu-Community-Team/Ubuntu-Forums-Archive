---
title: "Ubuntu Server 16.04 no ethernet"
date: 2017-12-09
forum: Networking &amp; Wireless
---

### Post by gllitton on 2017-12-09
Recently my computer running Ubuntu Server stopped being able to connect to the ethernet.

On boot it hangs on "A start job is running for Raise network interfaces" until it timeouts.

My /etc/network/interfaces contains:
    
```
source /etc/network/interfaces.d/*
    
    auto lo
    iface lo inet loopback
    
    auto enp1s0
    iface enp1s0 inet dhcp

```
ethtool enp1s0 returns the following

```
    Supported ports: [ TP MII ]
    Supported link modes:   10baseI/Half 10baseT/Full
                            100baseI/Half 100baseT/Full
                            1000baseI/Half 1000baseT/Full
    Supported pause frame use: No
    Suports auto-negotiation: Yes
    Advertised link modes:  10baseI/Half 10baseT/Full
                            100baseI/Half 100baseT/Full
                            1000baseI/Half 1000baseT/Full
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner dvertised link modes:  10baseI/Half 10baseT/Full
                                        100baseI/Half 100baseT/Full
                                        1000baseI/Half 1000baseT/Full
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 1000 Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                           drv probe ifdown ifup
    Link detected: yes
```

ifconfig enp1s0 returns this:

```
    enp1s0    Link encap:Ethernet  HWaddr 40:8d:5c:d7:a5:b4
              inet6 addr: fe80::428d:5cff:fed7:a5b4/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:0 (0.0 B) TX bytes:5426 (5.4 KB)

```
Running ifdown enp1s0 && ifup enp1s0 returns this:
    ```

    Listening on LPF/enp1s0/40:8d:5c:d7:a5:b4
    Sending on   LPF/enp1s0/40:8d:5c:d7:a5:b4
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 3 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 6 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 11 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 19 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 21 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 17 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 8 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 12 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 15 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 14 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 15 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 21 (xid=0x9505c211)
    DHPCDISCOVER on enp1s0 to 255.255.255.255 port 67 interval 18 (xid=0x9505c211)
    No DHCPOFFERS received
    No working leases in persistent database - sleeping
```

If I set a static IP i get "destination host unreachable" on all my pings

---

### Post by TheFu on 2017-12-12
Sounds like a cable or dhcp issue - if this is a home system, dhcp is usually provided by the router.  At work, contact the helpdesk.
 
--- edited out request for release.  Title has it.

---

