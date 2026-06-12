---
title: "Using source interface for specific VRF"
date: 2023-08-14
forum: Networking &amp; Wireless
---

### Post by seathorn on 2023-08-14
I made 3 separate VRFs in netplan, because I needed default route in each of them. 

To use my VRFs I can run commands with "ip vrf exec <vrf> <command>" and it is working fine, ie.:
```
ip vrf exec MYVRF ping 8.8.8.8
```

Unfortunately in one of my VRFs I have multiple interfaces and I need to define the outgoing interface for the traffic ie.:
```
ip vrf exec MYVRF ping 8.8.8.8 -I enp1s0f0.3025
```

All working fine, but some applications do not have option for selecting outgoing interface, so the default interface is used as source.
Can I somehow force the outgoing traffic to use a specific interface as source? I'm thinking of some global option or something.

---

