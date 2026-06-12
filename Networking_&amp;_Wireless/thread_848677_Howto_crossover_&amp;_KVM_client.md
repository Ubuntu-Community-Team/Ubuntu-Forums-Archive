---
title: "Howto crossover &amp; KVM client"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by NaughtyusMaximus on 2008-07-03
I'm having some problems getting my network to work properly with KVM.  I have two KVM servers, each with multiple network interfaces.  On each of them, eth0 connects to the local LAN, and eth1 is a crossover cable that goes directly to the other machine.

The /etc/network/interfaces files look like this:
KVM_SERVER_1:
```
auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

auto br1
iface br1 inet static
        address 10.0.50.1
        network 10.0.50.0
        broadcast 10.0.50.255
        netmask 255.255.255.0
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

KVM_SERVER_2:
```
auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

auto br1
iface br1 inet static
        address 10.0.50.2
        network 10.0.50.0
        broadcast 10.0.50.255
        netmask 255.255.255.0
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

The KVM client machines then have conf files which look like this (except w/ a differnet IP on the 2nd client):
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 10.0.50.3
netmask 255.255.255.0
broadcast 10.0.50.255
network 10.0.50.0
```

This seems to work ok when I first turn the machines on, I can usually ping all the four machines on the 10.0.50.0 subnet, but as soon as I start actually using them, one or both of the connections will die until I restart the guest machines again.  I've checked the crossover cable, and it appears to be fine, so I'm assuming there is something wrong with the configuration I've posted here.  Is there something obvious that I'm missing?

---

### Post by NaughtyusMaximus on 2008-07-03
Hm, apparently this isn't just a problem with the crossover setup.  I took out the eth1 devices on both clients, and set up drbd to work over eth0 on each machine.  They worked perfectly until around 8GB of data had been transferred from one to the other, and then the network interface on KVM Client 2 died.

ifup/ifdown on that machine does nothing.  The only way I could get it to work again was to reboot the client machine itself.

---

