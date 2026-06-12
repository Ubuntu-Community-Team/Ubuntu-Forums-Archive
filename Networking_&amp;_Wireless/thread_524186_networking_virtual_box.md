---
title: "networking virtual box"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by band-aid on 2007-08-12
I installed virtual box yesterday and have been playing around with an XP home guest but I need a bit of assistance in the networking department. Namely, creating a bridge.

I installed the bridge-utils package and have added the following to my /etc/network/interfaces. My goal is to create a bridge between my ipw3945 (eth1) and tap0 (the device that the VM will connect to). 

```

auto tap0
iface tap0 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        down ifconfig $IFACE down
        tunctl_user band-aid

auto br0
iface br0 inet dhcp
        bridge_ports all tap0

```

brctl show gives

```


bridge name     bridge id               STP enabled     interfaces
br0             8000.fa8341865c92       no              tap0


```

If I do sudo brctl addif br0 eth1, which adds eth1 to the bridge, my internet no longer works. 

For what its worth, I've never had good luck with bridges. I never did get networking over usb working with my zaurus using a bridge either.

---

