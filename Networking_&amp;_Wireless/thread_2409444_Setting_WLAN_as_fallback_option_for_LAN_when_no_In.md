---
title: "Setting WLAN as fallback option for LAN when no Internet access?"
date: 2019-01-02
forum: Networking &amp; Wireless
---

### Post by Dáire Fagan on 2019-01-02
using Powerline adaptor for my LAN connection, and the connection to my router drops intermittently. Until I replace this with a newer version, I would like to set Ubuntu to fall back on WLAN when the LAN connection fails / or LAN has no connection to the router or Internet access if possible.

I installed *ifmetric* so I can do something like* sudo apt-get install ifmetric *so I could lower the eth0 connection but I am not sure which is which. Looking at it now a I post, I am guessing perhaps *enp3s0* is eth0 as it already has a lower metric, and Ubuntu will automatically fall back on the WLAN once it is connected? If so, will it only do this if say a cable is unplugged, or will it detect no connection to the router / Internet?

```
dusf@contraption:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlx74d02bce7aa5
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx74d02bce7aa5



```

I disconnected the cable between the second Powerline adaptor and my router, and Ubuntu did fallback to WLAN, but this took several minutes, despite attempting to load a webpage in browser - can this be sped up?

---

