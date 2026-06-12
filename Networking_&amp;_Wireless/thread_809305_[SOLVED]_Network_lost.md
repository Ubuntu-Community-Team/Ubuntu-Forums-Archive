---
title: "[SOLVED] Network lost"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by alberto ferreira on 2008-05-27
I had my network running without problems, and then 2 months ago xp and vista lost internet connection, and I thought: well, maybe it's just a virus...

Then, about 3 days ago my ubuntu that was also working flawlessly lost connectivity, I don't have a clue of what is going on can someone help me?
I've got Ubuntu 7.10 and I use a wired connection with a router

---

### Post by mapes12 on 2008-05-27
Sounds like a router issue. Can we see:

```
sudo lshw -C network
```

```
sudo dhclient
```

```
ifconfig
```

```
cat /etc/resolv.conf
```

```
cat /etc/network/interfaces
```

And you may like to have a look through here:

[https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

---

### Post by T4K on 2008-05-27
Ironically enough I'm on Hardy and I must say everything was working fine until I ran update. My nic doesn't get an ip it seems. Stuck at 169... Model is Realtek RTL8166B/8111B

---

### Post by T4K on 2008-05-27
> **mapes12 said:**
> Sounds like a router issue. Can we see:

```
sudo lshw -C network
```

```
sudo dhclient
```

```
ifconfig
```

```
cat /etc/resolv.conf
```

```
cat /etc/network/interfaces
```

And you may like to have a look through here:

[https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

```
sudo lshw -C network
*-generic               
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: ff
       serial: 00:1d:7d:a2:e0:b4
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s

sudo dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1d:7d:a2:e0:b4
Sending on   LPF/eth0/00:1d:7d:a2:e0:b4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

 cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4970
#
### END INFO



nameserver 192.168.1.254


cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

---

### Post by mapes12 on 2008-05-27
> Listening on LPF/eth0/00:1d:7d:a2:e0:b4
Sending on   LPF/eth0/00:1d:7d:a2:e0:b4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Your DHCP service is sleeping!

Turn off the router. Remove all cables from it inc power, everything. Wait ten minutes. Reconnect everything. Then turn it back on again. Let it run its initialisation routine for a few minutes. When the lights are stable run ```
sudo dhclient
``` again and see if you get a valid DHCP connection.

---

### Post by alberto ferreira on 2008-05-27
Thanks everyone, but it was my fault, I'm very sorry. My computer went to be repaired and I have two ethernet ports, it seems that the internet connection is prepared to be run only in one of them. :( 

Best regards to everyone for answering so quickly!

---

### Post by T4K on 2008-05-27
> **mapes12 said:**
> Sounds like a router issue. Can we see:

```
sudo lshw -C network
```

```
sudo dhclient
```

```
ifconfig
```

```
cat /etc/resolv.conf
```

```
cat /etc/network/interfaces
```

And you may like to have a look through here:

[https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

> **mapes12 said:**
> Your DHCP service is sleeping!

Turn off the router. Remove all cables from it inc power, everything. Wait ten minutes. Reconnect everything. Then turn it back on again. Let it run its initialisation routine for a few minutes. When the lights are stable run ```
sudo dhclient
``` again and see if you get a valid DHCP connection.

If the router was sleeping. My laptop wouldn't have gotten an ip on a fresh ubuntu install.

---

