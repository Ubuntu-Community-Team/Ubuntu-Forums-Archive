---
title: "Ethernet Network interface not pinging IP"
date: 2016-08-29
forum: Networking &amp; Wireless
---

### Post by sudeep4 on 2016-08-29
Machine Details: Dell Optiplex 9020
OS: Dual Boot
1) Win 7 - network working fine
2) Ubuntu 14.04 - LAN interface eth0 is not able pull DHCP IP Address. Moreover while giving static IP, Gateway, Mask, DNS, it is not pinging the Gateway address.

sudo lshw -C network : gives proper output 
*-network
description: Ethernet interface
product: Ethernet Connection I217-LM
vendor: Intel corporation
capacity: 1Gbit/s
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4

please help!

---

### Post by The Cog on 2016-08-29
Please can you post the output of the commands 
```
ifconfig
```
and then 
```
sudo dhclient eth0
```

---

