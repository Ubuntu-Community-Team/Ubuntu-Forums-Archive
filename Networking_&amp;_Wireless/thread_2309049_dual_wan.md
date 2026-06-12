---
title: "dual wan"
date: 2016-01-07
forum: Networking &amp; Wireless
---

### Post by atux on 2016-01-07
hello. i have a mini itx pc with 3 network interfaces with ubuntu 12.04
for educational purposes i do need to make a working router in UBUNTU.
up to now i have the following setup:
eth0: 192.168.0.2/24 with gateway 192.168.0.1 (DSL router)
eth1:192.168.1.1/24 and serves as DHCP server

all PCs attached to eth1 get IPs from range 192.168.1.x network and then can access the Internet. eth0 does the NAT.
i have a second dsl connection available that i would like to use in load balance per session and failover in case something goes wrong. eth2 is available. 
...
after so many tries i did not succeed with the project and i would like a working solution if someone has anything, please.

---

