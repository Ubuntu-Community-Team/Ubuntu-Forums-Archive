---
title: "Setting up Eth Port Aggregation to achieve double throughput"
date: 2021-06-25
forum: Networking &amp; Wireless
---

### Post by nirxy on 2021-06-25
Hello folks,
I recently managed to setup LACP bonding using Netplan on ubuntu server 21.04, by bonding two 1gb eth ports. 
Later I discovered that it still limits throughput from a single client to 1gb, and LACP throughput is only increased for two or more clients.

Is there a way to setup port bonding differently that will achieve ~2gb throughput even from a single client? 
My router is RAX200 and supports either LACP 802.3ad or Static LAG.

Thank you!

---

### Post by TheFu on 2021-06-25
In general, no, but there are exceptions.

Some application network protocols CAN merge bandwidth, provided all the application versions on the clients and the servers run a version of that application protocol which provides the support.  For example, multi-channel NFS or multi-channel SMB can.

With NFS on Linux kernels 5.3 and later, the client can request multiple channels easily:
```
mount -t nfs -o ro,nconnect=16 198.18.0.100:/datasets /mnt/datasets
```
Provided the NICs are connected to a single VIP, it will work.

Can also test this using iperf3 with some options to use multiple connections, so you can see the single NIC limitation be overcome when multiple are used or with some drivers, using multiple connections allows other cores to be used for traffic and bandwidth increases. This is an issue with BSD and some Intel NIC drivers, for example.  They appear to be single threaded, unless multiple connections are open, then the extra cores can become involved multiplying throughput.

I think smb can do the same.

I vaguely recall trouble could happen if all the NICs involved didn't have the same IPv4 and IPv6 enabled.  So don't try to use 4 NICs, but with 2 IPv4-only configurations and 2 with both IPv4 and IPv6 configs.

Realistically, the easy answer is to switch to 5Gbps or 10Gbps networking. We'll all be there at home eventually.

---

### Post by nirxy on 2021-06-26
Thank you for the detailed answer!

---

