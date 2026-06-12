---
title: "bridge stops working suddenly"
date: 2013-11-30
forum: Networking &amp; Wireless
---

### Post by swapnil-indore on 2013-11-30
Hi,

I am using Ubuntu 10.04. I  have created 2 tagged vlans on eth0 and bridged one vlan with eth1. It works well but suddenly stops working and I just have to either reboot the system or delete and create the bridge again. PC connected on eth1 stops communicating on the vlan. I don't see any related logs and not able to debug what the issue is. This is my bridge configuration

```
ifconfig eth0 up
/sbin/vconfig add eth0 1033
/sbin/vconfig add eth0 810


ifconfig eth0.810 172.16.1.1 netmask 255.255.0.0 up




brctl addbr br-vlan
ifconfig br-vlan up
brctl addif br-vlan eth1
brctl addif br-vlan eth0.1033
ifconfig eth0.1033 0.0.0.0 up
ifconfig eth1 0.0.0.0 up



ifconfig br-vlan 192.168.1.1 netmask 255.255.255.0 up


```

---

