---
title: "Configuring a dhcp server in Edgy"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by hairshirt on 2006-10-28
Right gang,

I've just installed Edgy server, sorted out the vi/vim thing.

The server has two network cards.  One: eth0 is for external thought the router the other: eth1, I want to configure as dhcp.

I've installed udhcpd and dhcp3-server.  Neither of them work for one of two or both reasons:

1. Can't seem to configure eth1 in: vi /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.100
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.100

auto eth1
iface eth1 inet dhcp

2. Can't start the .conf files for either udhcpd or dhcp3-server.  I also installed webmin and eth1 is not listed as an option for network cards.

When I # vi /etc/dhcp3/dhcpd.conf I get a blank screen telling that a new file is going to be created.

Any help? :confused:

---

### Post by dannyboy79 on 2006-11-01
well I am trying to set this up currently myself, well I want to try but I haven't started yet. I have been doing a lot of reading and from what you have posted and told me, you want your eth1 to be the interface that you''l connect to your lan. well according to your interfaces config, you're telling eth1 that it should use dhcp to GET IT'S OWN IP from a dhcp server, well, is there a dhcp server hooked up before eth1? I think you need to make your eth0 your router as well as your dhcp server so that eth1 can get's it ip from it. I am not sure but it's sounds logical correct?

---

