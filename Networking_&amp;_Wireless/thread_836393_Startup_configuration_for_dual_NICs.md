---
title: "Startup configuration for dual NICs"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by ba_rich on 2008-06-21
I'm trying to configure two Ethernet interfaces as follows:

  eth0 - Connected to our internal network with a static IP address
         of 192.168.0.1. This interface will be the gateway to the
         Internet.

  eth1 - Connected to the router. Uses DHCP to get its address.
         The router address is 192.168.0.1.

The /etc/network/interfaces file looks like this:

  # Loopback address
  auto lo
  iface lo inet loopback
    address 127.0.0.1
    netmask 255.0.0.0
	
  # The connection to the Internet. Get an IP address automatically.
  auto eth1
  iface eth1 inet dhcp
	
  # The gateway for the internal network.
  auto eth0
  iface eth0 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255

When the PC boots up, the routes look like this:

  $ ip route show
  192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.1
  192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.135
  169.254.0.0/16 dev eth0  scope link  metric 1000

If I change the eth0 address in etc/network/interfaces to 192.168.0.2 and restart the networking, the routes look like this:

  $ sudo /etc/init.d/networking restart
    ....
  $ ip route show
  192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.135
  192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.2
  169.254.0.0/16 dev eth1  scope link  metric 1000

If I restart the networking a second time, the routes are what I want:

  $ sudo /etc/init.d/networking restart
    ....
  $ ip route show
  192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.135
  192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.2
  169.254.0.0/16 dev eth1  scope link  metric 1000
  default via 192.168.0.1 dev eth1  metric 100

I can now change the eth0 address to 192.168.0.1 and the routes are correct:

  $ sudo /etc/init.d/networking restart
    ....
  $ ip route show
  192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.135
  192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.1
  169.254.0.0/16 dev eth1  scope link  metric 1000
  default via 192.168.0.1 dev eth1  metric 100

How do I make the network come up in this configuration at startup?

---

### Post by ba_rich on 2008-06-21
The problem was apparently caused by no cable being plugged into eth0. After rebooting with a cable plugged in, the routing is correct.

Now it reboots correctly even if no cable is plugged in.

---

