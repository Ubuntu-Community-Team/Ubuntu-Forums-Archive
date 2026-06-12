---
title: "No Network At all?"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by TheRobohobo on 2006-07-20
I've tryed to configure my computer to connect to my router multiple times, but it doesn't seem to be doing anything. I have a belkin wireless-g router, and I'm connecting via ethernet, I set the thing up myself, so I know what all the setting should be, but I still can't connect.

---

### Post by Paerez on 2006-07-20
can you post me the output to the following commands:
```
sudo ifconfig eth0
sudo dhclient eth0
```
replace eth0 with your ethernet device (its probably eth0, though).

---

### Post by TheRobohobo on 2006-07-20
> **Paerez said:**
> can you post me the output to the following commands:
```
sudo ifconfig eth0
sudo dhclient eth0
```
replace eth0 with your ethernet device (its probably eth0, though).
```
eth0      Link encap:Ethernet  HWaddr 00:16:17:1C:5F:7B
          inet6 addr: fe80::216:17ff:fe1c:5f7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:176 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8254 (8.0 KiB)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xe000

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:16:17:1c:5f:7b
Sending on   LPF/eth0/00:16:17:1c:5f:7b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by Paerez on 2006-07-20
It seems like DHCP is not set up on your router correctly. Double check the router settings.

---

### Post by TheRobohobo on 2006-07-20
Everything else seems in working order, I am using DHCP for the rest of the computers on my network, all running windows.

---

### Post by Paerez on 2006-07-20
you don't have any mac filtering or anything?

---

