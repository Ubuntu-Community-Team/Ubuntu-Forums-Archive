---
title: "Iperf to Multiple IP's on one machine"
date: 2014-08-09
forum: Networking &amp; Wireless
---

### Post by chase6 on 2014-08-09
First off, I am working in a DOCSIS lab networking environment, so that changes a few things. What I need to do is push data across a large group of multiple cable modems - preferably to just a few machines. Preferred setup would be to push data over 40 cable modems, so looking at 40 different IP addresses, on a single subnet. I would ~like~ to do this with one or just a few virtual machines, but I am running into the multiple NIC's on the same subnet issue that seems to get the best Google answer of "don't do it". I know this testing can be done with 40 different virtual machines, I'm just trying to limit the initial setup time as we are pressed for it already. Each NIC will have to be able to respond to a remote subnet from itself, so it calls for multiple routing tables. I cannot use VLAN interfaces, as they use the same MAC address, which the CMTS will ARP to a single modem, nulling the test. Any ideas other than spend an entire day building VMs?

---

