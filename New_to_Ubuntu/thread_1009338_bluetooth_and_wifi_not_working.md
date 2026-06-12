---
title: "bluetooth and wifi not working"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by rkakkar on 2008-12-12
kdebluetooth4 doesn't show/do anything and neither is my wifi working (both enabled by the same button on my lappy). any ideas?

---

### Post by Peter09 on 2008-12-12
start with wifi

can you post the output of

```
lshw -C network
```

and 

```
ifconfig
```

---

### Post by rkakkar on 2008-12-14
> **Peter09 said:**
> start with wifi

Kubuntu is detecting the wireless network with full signal strength. But when I click on it to connect, nothing happens.

> **Peter09 said:**
> 
can you post the output of

```
lshw -C network
```


```
$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:29:9d:c0:88
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:37:bc:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:25:c2:5c:bd:92
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

> **Peter09 said:**
> 
and 
```
ifconfig
```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:29:9d:c0:88
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:e4600000-e4620000

eth1      Link encap:Ethernet  HWaddr 00:21:00:37:bc:4d
          inet6 addr: fe80::221:ff:fe37:bc4d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:204
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4392 (4.3 KB)  TX bytes:4392 (4.3 KB)
```

Any ideas?

Cheers.

---

### Post by Peter09 on 2008-12-14
OK, you seem to have a working wireless card but no connection.

When you left click on the network icon what do you see?

---

### Post by rkakkar on 2008-12-15
> **Peter09 said:**
> OK, you seem to have a working wireless card but no connection.

When you left click on the network icon what do you see?


check the screenshot. nothing happens when i click on the connection though.

---

### Post by AlanR8 on 2008-12-15
I assume you went through the Knetworkmanager "wizard"? Click on Edit connection and then provide any passwords/security your router needs.

---

### Post by rkakkar on 2008-12-15
> **AlanR8 said:**
> I assume you went through the Knetworkmanager "wizard"? Click on Edit connection and then provide any passwords/security your router needs.

Its an open connection with no password/security. It work in windows and doesn't need a key. Knetworkmanager automatically detected this connection.

---

