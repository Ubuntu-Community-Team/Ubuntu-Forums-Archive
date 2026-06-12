---
title: "Connect two network devices"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by NewWaves on 2006-09-30
I'm trying to connect eth0 and wlan0 together so I can run a crossover cable from eth0 to another network card on another computer... wlan0 would be the source to the WAN.  Anyway I can do this?

---

### Post by kipeloff on 2006-09-30
It's possible, you have to enable NAT (src-nat or masquerading) on the Ubuntu worskstation with two network interfaces. To accomplish you scenario,
- set appropriate configuration to the wlan interface (IP address, gateway configuration, etc.);
- set private address to the eth0 interface, e.g. 192.168.0.1/24, than set the address within the same subnet for the second workstation, e.g. 192.168.0.2.
- enable NAT (masquerading), infromation about masquerading,
[https://help.ubuntu.com/ubuntu/serverguide/C/firewall-configuration.html](https://help.ubuntu.com/ubuntu/serverguide/C/firewall-configuration.html)
- 192.168.0.1 will be the gateway for the second workstation.

---

