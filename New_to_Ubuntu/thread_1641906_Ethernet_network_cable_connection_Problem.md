---
title: "Ethernet network cable connection Problem"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by speed86 on 2010-12-09
Hi,

using Ubuntu 10.10

My older laptop is a Dell Inspiron 6400 and at home everytime I plug in the *Ethernet* network [I]cable I get nothing,

I tried changing the cable....didn't work
then I went to a netcafe and plugged it in there and it worked fine the wired thing is he has the same router as me CISCO linksys 

I tried to avoid this problem by using WIFI but it seems to disconnect and reconnect every 2 Min

Note my newer laptop Inspiron 1545 has none of these problems with my router or anywhere else.....

any ideas?
[/I]

---

### Post by Hippytaff on 2010-12-09
if you post the results of the following commands it will help diagnose the problem
```

sudo lshw -C Network

```
```

ifconfig

```
```

lspci | grep -i eth

```

Not that I'll know how to fix it, but someone here will (probably) :-)

Secondly are you sure your router/switch is working ok, and that your network is up and running (ie working with windows is it?)

---

### Post by speed86 on 2010-12-09
Thanks 4 the reply, yes everthing else is working perfectly with router windows and another pc running Ubuntu.

sudo lshw -C Network
```

 *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 01
       serial: 00:16:cf:99:f1:44
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.104 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:efdfc000-efdfffff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1-eth0
       version: 02
       serial: 00:15:c5:b8:28:7c
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:ef9fe000-ef9fffff


```

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:16:cf:99:f1:44  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe99:f144/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1033 errors:0 dropped:0 overruns:0 frame:1918
          TX packets:1032 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:963217 (963.2 KB)  TX bytes:193417 (193.4 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


```
lspci  | grep -i eth


```

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)


```

---

### Post by Hippytaff on 2010-12-09
Broadcom - try going to system -> administration -> additional drivers

if there are drivers there to install (broadcom ones) then do that...did you upgrade recently?

---

