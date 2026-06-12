---
title: "Intel 3945ABG won't connect to wireless."
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by Nem1976 on 2008-07-25
I have a Acer Laptop that I'm tring to get connected to my work wireless network.  I'm using wicd for my network manager and the laptop sees the wireless ssid but if I try and connect it just sits there saying trying to obtain ip address.  I can boot into windows and use the intel card and get connected.  If I put a netgear pcmcia card in and I'm able to connect up just fine.    I can go home and the intel works fine but just this specific network it doesn't like.  

I just can't get the Intel card to connect under ubuntu on this specific network.

Any suggestions would be helpful.

Thanks
Nem

---

### Post by PinkFloyd102489 on 2008-07-25
The Intel card is supported natively, so it should be working. Check if the package wpasupplicant is installed.


Also post the output of this command:

```
lshw -C Network
```

---

### Post by Nem1976 on 2008-07-25
The access points I'm trying to connect to are a number of Cisco Aironet 350's.

Here is the output of lshw -C Network

```
nem@nem-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:69:b8:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:af:b2:58
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

```

---

### Post by imdano on 2008-07-26
Is there any kind of encryption on the network?

---

### Post by Nem1976 on 2008-07-26
> **imdano said:**
> Is there any kind of encryption on the network?

No encryption what so ever.  

We have an authenticate server that is running radius on it.  I have tried to static Ip assignment and I still can't get connected.  But if I boot to Vista(dual boot) I can connect with the intel card just fine.  This has me completely stumped why this is happening.

---

### Post by jsonder on 2008-07-26
> **Nem1976 said:**
> The access points I'm trying to connect to are a number of Cisco Aironet 350's.

Here is the output of lshw -C Network

```
nem@nem-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:69:b8:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:af:b2:58
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

```

The only difference that I see is in the configuration (Dell Inspiron E1505 using 8.04.01 and wicd because Network Manager loses the WPA passphrase)  I've got an IP assigned via DHCP:

dad@dad-laptop:~$ sudo lshw -C Network
[sudo] password for dad: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:26:ed:03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.136 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:11:3f:69
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
dad@dad-laptop:~$

---

### Post by Nem1976 on 2008-07-27
Ya this is very strange.  This wireless works fine at other locations with the intel card it's just doesn't seem to like talking to the cisco equipment when using linux.

---

### Post by rahul_rocks on 2008-07-27
> **Nem1976 said:**
> Ya this is very strange.  This wireless works fine at other locations with the intel card it's just doesn't seem to like talking to the cisco equipment when using linux.
No encryption what so ever.

We have an authenticate server that is running radius on it. I have tried to static Ip assignment and I still can't get connected. But if I boot to Vista(dual boot) I can connect with the intel card just fine. This has me completely stumped why this is happening.





try to configure your router with wep with 64bit key 
and try to connect because with authenticate server that is running radius sometimes it will not authenticate

---

