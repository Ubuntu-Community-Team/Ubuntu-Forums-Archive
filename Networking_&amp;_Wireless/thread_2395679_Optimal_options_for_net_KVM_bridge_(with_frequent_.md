---
title: "Optimal options for net KVM bridge (with frequent hot-pug Ethernet)"
date: 2018-07-05
forum: Networking &amp; Wireless
---

### Post by linuksguru on 2018-07-05
Hi !

I have fanless mini PC with 10 Ethernet interfaces and KVM host which I use for testing routers.
8 Ethernet interfaces bridged to KVM, 1 used for KVM host itself.
Juggling Ethernet connections (connecting/disconnecting cables) time to time leads to host OS hard crash (complete freeze), or guest OS freeze.
After first freeze I changed KVM Ethernet devices from virtio to rtl, it didn’t solve the problem. 
Bridges defined as shown below. May be there are other suitable options for bridges I'm not aware about ?

Thanks in advance for any suggestion(s).

```

auto br2_LTC1
iface br2_LTC1 inet manual
   bridge_ports enp16s0
   bridge_stp off
   bridge_waitpot 0
   bridge_fd 0.0
auto br2_BTC2
iface br2_BTC2 inet manual
   bridge_ports enp17s0
   bridge_stp off
   bridge_waitpot 0
   bridge_fd 0.0
auto br2_DMZ
iface br2_DMZ inet manual
   bridge_ports enp18s0
   bridge_stp off
   bridge_waitpot 0
   bridge_fd 0.0
auto br2_INT
iface br2_INT inet manual
   bridge_ports enp19s0
   bridge_stp off
   bridge_waitpot 0
   bridge_fd 0.0

```

---

