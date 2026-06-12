---
title: "PPTP VPN with static IP address on VPN interface (ppp0)"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by unicoletti on 2007-10-12
I am on Ubuntu 7.0.4 and can connect to most VPNs with NetworkManager.
Unfortunately one of the sites I need to connect requires that I have a fixed IP address on the VPN interface ppp0  (not on my LAN interface).

I have also tried to write:

10.1.1.1:

inot the custom ppp options in the NetworkManager dialog, but without success.

I have then tried in other ways, with pptpconfig and have extensively googled the internet but I can't figure out how to set a static ip address.

Anyone knows how and if it can be done?

Many thanks in advance,
Umberto

---

### Post by bvmou on 2007-10-12
To set a static IP address you can change your /etc/network/interfaces file (with the command "sudo gedit /etc/network/interfaces") to read something like:

```
allow-hotplug eth0
auto eth0
iface eth0 inet static
        address 192.168.1.23
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

Right now it probably looks like:

auto eth0
iface eth0 inet dhcp

The relevant bit for you may be related you your point about 10.0.0.1, that is the gateway of a lot of corporate networks, it is not inherently different from the one used in other local networks but the part that would be changed to 10.0.0.1 if that is what you're being told is the gateway.

I am not a pro at this at all so use this mainly as a google enhancer, let us know how it goes for you.

---

