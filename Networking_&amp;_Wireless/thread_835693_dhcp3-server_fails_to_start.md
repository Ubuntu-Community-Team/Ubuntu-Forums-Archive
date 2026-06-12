---
title: "dhcp3-server fails to start"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by Leebria on 2008-06-20
Hi everyone, I've seen several posts here concerning this issue yet I can't seem to find a solution out of them! This i my first time setting up a dhcp server on Linux so I'm hoping there is a simple fix.

I've installed dhcp3-server using:  sudo apt-get install dhcp3-server

Here is my dhcpd.conf file:

## start config file ##
  authoritative;
  ddns-update-style none;
  default-lease-time 86400;
  max-lease-time 604800;

  subnet 192.168.100.0 netmask 255.255.255.0 {
    range 192.168.100.100 192.168.100.110;
    option domain-name "ubuntu";
    option domain-name-servers 192.168.100.10;
    option broadcast-address 192.168.100.255;
    option routers 192.168.100.1;
  }
## end config file ##

My /etc/default/dhcp3-server is set to:  INTERFACES="eth1"

My /etc/network/interfaces:

## start interfaces ##
  # This file describes the network interfaces available on your system
  # and how to activate them. For more information, see interfaces(5).

  # The loopback network interface
  auto lo
  iface lo inet loopback

  # The primary network interface
  auto eth1
  iface eth1 inet dhcp
  #address 192.168.100.10
  #netmask 255.255.255.0
  #hostname ubuntu
## end interfaces ##

When I try starting dhcp3-server using:  /etc/init.d/dhcp3-server start

it gives the error:

  dhcpd self-test failed. Please fix the config file.
  The error was:

Now I've been looking into the no error display bug and found a fix at [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/94804]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/94804") , however, I'm confused about this. Does it go into the dhcpd.conf file? Thanks for any help!

---

### Post by jimv on 2008-06-20
I'm pretty sure that you need to assign eth1 a static address.  You have it set to use DHCP:

```
# The primary network interface
auto eth1
iface eth1 inet dhcp
#address 192.168.100.10
#netmask 255.255.255.0
#hostname ubuntu
```

Should be:

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.100.10
gateway 192.168.1.1        (or whatever your internet gateway is)
netmask 255.255.255.0
network 192.168.100.0
broadcast 192.168.100.255
```

Oh yeah, and you can't have any other DHCP servers on the network.  So if your router has a DHCP server, you need to turn it off.

---

### Post by Leebria on 2008-06-20
That was it, thanks!

---

