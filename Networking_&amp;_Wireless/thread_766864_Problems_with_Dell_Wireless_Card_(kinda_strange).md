---
title: "Problems with Dell Wireless Card (kinda strange)"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by nelsoncaballero on 2008-04-25
Hi to all,

Well I'm a Ubuntu newbie... I'm using Linux since a while (Fed*ra and R*d H*t), but first timer in desktop linux.
I'm using Ubuntu 8.04 (installed using Wubi... just wonderfull :KS, don't need to partition my HDD).
Everything seems to be working fine except the Wireless Card, I do some research and i found this...

root@nelcab-laptop:/home/nelcab# lshw -C network
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ec:bf:2c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.0.0.27 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:0f:b9:83
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

I don't know why it detects on Phy ID 2 another network because it only have a unique Wireless Card (the one on the ID 0).
And so.. when I do a iwconfig it detects this...

root@nelcab-laptop:/home/nelcab# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

... like the wlan0 is shutdown.


root@nelcab-laptop:/home/nelcab# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:22:ec:bf:2c  
          inet addr:10.0.0.27  Bcast:10.0.0.31  Mask:255.255.255.224
          inet6 addr: fe80::214:22ff:feec:bf2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3397385 (3.2 MB)  TX bytes:510455 (498.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101900 (99.5 KB)  TX bytes:101900 (99.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:0f:b9:83  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CE-0F-B9-83-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


and I have here a wlan0 and wmaster0 (which I don't know why).

Can anyone have an idea how to get it work?  I was wondering at the Laptop compatibility wiki of Ubuntu and seems that they don't have any issue with it.  
Thanks for any help you can provide me.
Best regards,

P.S. BTW, Wireless Card is enable :)

Nelson

---

### Post by Tim Sharitt on 2008-04-25
Did you install the driver firmware? Try:
```
sudo apt-get install b43-fwcutter
```

---

### Post by nelsoncaballero on 2008-04-25
That was it... thank you very much.
Best regards,

Nelson


> **Tim Sharitt said:**
> Did you install the driver firmware? Try:
```
sudo apt-get install b43-fwcutter
```

---

