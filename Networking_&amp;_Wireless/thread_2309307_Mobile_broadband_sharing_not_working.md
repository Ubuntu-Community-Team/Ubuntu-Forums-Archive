---
title: "Mobile broadband sharing not working"
date: 2016-01-09
forum: Networking &amp; Wireless
---

### Post by petar.kresimir.cul on 2016-01-09
Hi. I followed tutorials to setup my mobile broadband to share it's Internet over Ethernet to my router and it doesn't works. On devices that I'm using to test the connection I receive DNS_PROBE_FINISHED_NO_INTERNET message. Can anyone help me out?

This is my ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:11:25:d2:55:59  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fed2:5559/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8965 (8.9 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:cc:9e:01  
          inet6 addr: fe80::212:f0ff:fecc:9e01/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4096 (4.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:144520 (144.5 KB)  TX bytes:144520 (144.5 KB)

wwan0     Link encap:Ethernet  HWaddr 8e:25:f2:1e:a2:86  
          inet addr:10.216.142.247  Bcast:10.216.142.255  Mask:255.255.255.240
          inet6 addr: fe80::8c25:f2ff:fe1e:a286/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11283173 (11.2 MB)  TX bytes:941897 (941.8 KB)
```

This is my lshw -C network

```

PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:11:25:d2:55:59
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5751m-v3.40a ip=10.42.0.1 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:90100000-9010ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:cc:9e:01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
       resources: irq:21 memory:90301000-90301fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: wwan0
       serial: 8e:25:f2:1e:a2:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=qmi_wwan driverversion=22-Aug-2005 fi


```
This are my settings for the wired connection 1
[IMG]http://i.imgur.com/chDT5eb.png[/IMG]
[IMG]http://i.imgur.com/Z0oIWf7.png[/IMG]

This is my broadband
[IMG]http://i.imgur.com/L52Rrc9.png[/IMG]

And this is my network info
[IMG]http://i.imgur.com/PkVqf6F.png[/IMG]
[IMG]http://i.imgur.com/Z6r8MwZ.png[/IMG]

What am I doing wrong?

---

