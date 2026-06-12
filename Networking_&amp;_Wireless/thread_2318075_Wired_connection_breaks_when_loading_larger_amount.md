---
title: "Wired connection breaks when loading larger amounts of data"
date: 2016-03-22
forum: Networking &amp; Wireless
---

### Post by Thomas_van_Wagenin on 2016-03-22
Hi,

My title is a little vague as I am not entirely sure of the exact nature of my connection issue. At first glance everything seems to be in order; I am connected to "Wired connection 1". I can ping google.com and usually load google.com in Firefox. When I try to load a larger page it takes a long time before saying "Server not found". I can no longer load any other pages nor can I ping google.com. If I reconnect the ethernet cable I can again load and ping google.com.

I just installed 14.04. I also have Windows 8 on this computer.

My Windows laptop is able to connect via the ethernet cable. Yes I turned off the wifi. I also tried a new ethernet cable and that works for my laptop, same problem on my Ubuntu computer. Rebooting my router did nothing.

I am currently somewhere in the realm of is my driver working?

Here are my settings. If there is any other information I can provide please let me know.

sudo ethtool eth0
```

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: Symmetric Receive-only
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Current message level: 0x000060e4 (24804)
                   link ifup rx_err tx_err hw wol
    Link detected: yes

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 7c:05:07:91:5b:01  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::7e05:7ff:fe91:5b01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24349 errors:17383 dropped:0 overruns:17383 frame:0
          TX packets:8130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7492383 (7.4 MB)  TX bytes:842686 (842.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1661161 (1.6 MB)  TX bytes:1661161 (1.6 MB)

```

sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 08
       serial: 7c:05:07:91:5b:01
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.2.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:31 memory:f7c00000-f7c3ffff ioport:e000(size=128)

```

nm-tool
```

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        7C:05:07:91:5B:01

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.254

    DNS:             192.168.2.254
    DNS:             195.241.77.55
    DNS:             195.241.77.58

```

cat /etc/network/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

cat /etc/NetworkManager/NetworkManager.conf
```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

```

cat /var/lib/NetworkManager/NetworkManager.state
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

I changed /etc/network/interfaces to
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```
and ran sudo /etc/init.d/networking restart but this did not have any effect.

Any help is gladly appreciated!

---

