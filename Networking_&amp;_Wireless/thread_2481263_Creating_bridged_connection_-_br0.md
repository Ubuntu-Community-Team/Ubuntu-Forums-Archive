---
title: "Creating bridged connection - br0"
date: 2022-11-23
forum: Networking &amp; Wireless
---

### Post by securitydad on 2022-11-23
I want to bridge two connections to reflect traffic on Ubuntu 22.04.

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04 LTS
Release:    22.04
Codename:    jammy
```

Previously I used the contents of the /etc/network/interfaces file to create the bridge on start-up.

```
#interfaces file used by ifup and ifdown

auto lo
iface lo inet loopback

# Bridge two interfaces
#auto br0
#iface br0 inet dhcp
#bridge_ports enp0s31f6 enp45s0
#bridge_stp off
#bridge_fd 0
#bridge_maxwait 0
#post-up ifconfig enp0s31f6 mtu 1520
#post-up ifconfig enp45s0 mtu 1520

```

However, this no longer functions with the desired results.

How can I create a Bridge in Ubunut 22.04 reliably?  I have tried the NetPlan (results were horrible), and the NMCLI wasn't pretty as well.

Any suggestions?

---

