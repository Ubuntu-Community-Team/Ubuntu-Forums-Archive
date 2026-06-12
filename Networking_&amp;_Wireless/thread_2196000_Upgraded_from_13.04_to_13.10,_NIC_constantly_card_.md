---
title: "Upgraded from 13.04 to 13.10, NIC constantly card up and down"
date: 2013-12-27
forum: Networking &amp; Wireless
---

### Post by miket-r on 2013-12-27
I can hardly use my computer after upgrading, *wired* network connection is constantly lost and restored.  These messages appear hundreds of times in /var/log/kern.log (600 times in ~20 minutes):
Dec 27 09:33:26 AVA-pc055 kernel: [ 1459.138797] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
Dec 27 09:33:26 AVA-pc055 kernel: [ 1459.138805] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
Dec 27 09:33:26 AVA-pc055 kernel: [ 1459.408653] e1000e: eth0 NIC Link is Down

ifconfig:
eth0      Link encap:Ethernet  HWaddr 88:51:fb:4b:47:e9  
          inet addr:192.168.0.38  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8a51:fbff:fe4b:47e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9031855 (9.0 MB)  TX bytes:3659333 (3.6 MB)
          Interrupt:20 Memory:f7c00000-f7c20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2161767 (2.1 MB)  TX bytes:2161767 (2.1 MB)

lshw -c net:
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 88:51:fb:4b:47:e9
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4 ip=192.168.0.38 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:f7c00000-f7c1ffff memory:f7c39000-f7c39fff ioport:f080(size=32)



Any suggestions greatly appreciated.

---

