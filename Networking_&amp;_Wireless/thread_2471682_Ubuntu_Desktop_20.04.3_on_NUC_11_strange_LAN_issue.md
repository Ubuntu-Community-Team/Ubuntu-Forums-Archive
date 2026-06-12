---
title: "Ubuntu Desktop 20.04.3 on NUC 11: strange LAN issue"
date: 2022-02-06
forum: Networking &amp; Wireless
---

### Post by glc650 on 2022-02-06
Hi,

I have a fresh (2 day old) install of Ubuntu Desktop 20.04.3 on an Intel 11 NUC (NUC11PAHi7).  The WiFi interface is disabled in the BIOS so the only physical network interface on this machine is the NUC's built-in 1gbe NIC (enp88s0).  This NIC is on two different subnets (VLANs).  Here is my netplan config:

```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: networkd
  ethernets:
    enp88s0:
      mtu: 9000
      dhcp4: false
  vlans:
    enp88s0.100:
      mtu: 9000
      dhcp4: false
      addresses: [10.0.0.3/24]
      gateway4: 10.0.0.254
      nameservers:
        addresses: [1.1.1.1,1.0.0.1]
      id: 100
      link: enp88s0
    enp88s0.101:
      mtu: 9000
      dhcp4: false
      addresses: [10.1.0.3/24]
      nameservers:
        addresses: [1.1.1.1,1.0.0.1]
      id: 101
      link: enp88s0
```

ip r output:
default via 10.0.0.254 dev enp88s0.100 proto static
10.0.0.0/24 dev enp88s0.100 proto kernel scope link src 10.0.0.3
10.1.0.0/24 dev enp88s0.101 proto kernel scope link src 10.1.0.3

For some reason I am unable to SSH/VNC into this machine from the 10.1.0.0/24 network to the 10.0.0.3 interface  (specifically from my MacBook Pro's WiFi at 10.1.0.32).  It just times out (the firewall sitting in-between these subnets has this traffic permitted & ufw is disabled on Ubuntu).  SSH/VNC work just fine when on the same subnet (so 10.1.0.32 to 10.1.0.3 or 10.0.0.0/24  to 10.0.0.3).

Thanks,

->g.

---

