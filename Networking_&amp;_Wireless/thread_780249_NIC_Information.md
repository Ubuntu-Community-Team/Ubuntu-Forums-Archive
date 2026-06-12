---
title: "NIC Information"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Gillette on 2008-05-03
I'm getting DSL next week but don't know if my ethernet card will work with Ubuntu 7.10. 

I used the ifconfig eth0 command but don't know what the results mean:

eth0      Link encap:Ethernet  HWaddr 00:50:BF:A5:33:4D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x1400 

I did the ifconfig -a also:

eth0      Link encap:Ethernet  HWaddr 00:50:BF:A5:33:4D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:209.112.150.32  P-t-P:209.193.63.144  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3322304 (3.1 MB)  TX bytes:702817 (686.3 KB)

I tried this command too:  ip addr show eth0
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:50:bf:a5:33:4d brd ff:ff:ff:ff:ff:ff

Will this NIC work with UBUNTU next week? Do I need to get a different NIC or do something with the NDISWRAPPER.

---

### Post by chili555 on 2008-05-03
Looks perfectly fine to me. You might also look at ```
sudo ethtool eth0
sudo lshw -C network
```Based on what I see here, I think you will be fine.

---

### Post by Gillette on 2008-05-03
Here is the result of sudo ethtool eth0

Settings for eth0:
No data available

Here are the results for sudo lshw -C network
 *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 11
       bus info: pci@0000:00:11.0
       logical name: eth0
       version: 11
       serial: 00:50:bf:a5:33:4d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes

This is on an elderly Gateway Performance 600.

---

### Post by Gillette on 2008-05-03
I tried this command also to show the driver:

sudo ethtool -i eth0

Results:

driver: tulip
version: 1.1.15
firmware-version: 
bus-info: 0000:00:11.0

---

### Post by chili555 on 2008-05-04
> I'm getting DSL next weekPlug it in and go. Your ethernet interface looks healthy and ready to embrace DSL. Have fun!

---

### Post by Gillette on 2008-05-05
DSL got hooked up today and Ubuntu 7.10 connected nicely without any problems to the internet. Thanks very much for the help.

---

