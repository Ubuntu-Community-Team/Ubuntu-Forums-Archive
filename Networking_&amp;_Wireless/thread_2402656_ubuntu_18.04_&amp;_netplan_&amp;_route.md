---
title: "ubuntu 18.04 &amp; netplan &amp; route"
date: 2018-10-03
forum: Networking &amp; Wireless
---

### Post by dejanbukovec on 2018-10-03
I have small problem after upgrade(new install) from 16.04 to 18.04 with network configuration...
My old interface settings look like this:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d
 
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet dhcp
 
auto eth0.3999
iface eth0.3999 inet static
    address 10.132.25.19
    netmask 255.255.0.0
    vlan-raw-device eth0
 
up route add -net 224.0.0.0 netmask 240.0.0.0 dev eth0.3999



```

Because this is my first setup which use netplan for configuring network settings I have little problem to make it work... I don't know how to correctly add route in netplan without gateway... For now Im configure eth0 interface and vlan eth.3999 but now don't know how to add route to this vlan interface...
My current netplan configuration look like this:
```

network:
    version: 2
    ethernets:
        eth0:
            dhcp4: true
 
    vlans:
        eth0.3999:
            id: 3999
            link: eth0
            dhcp6: no
            accept-ra: no
            addresses: [10.132.25.19/16]



```

Thanks for any help.

---

### Post by dejanbukovec on 2018-10-05
I don't need help anymore, Im solve problem.

---

### Post by QIII on 2018-10-05
Would you please post the solution?

The Forums are for the community's benefit, not only for the benefit of any individual.  As you have left it, you have not allowed the community to learn.

Thanks.

---

