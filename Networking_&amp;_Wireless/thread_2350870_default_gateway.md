---
title: "default gateway"
date: 2017-01-28
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2017-01-28
Last time i tried messing with the gateway settings i broke remote login, royal pain that was being this server has no head

This server has 2 NICs each with 2 ports
I had 2 spare so i set them up for backup purposes ([FONT=courier new]eno1[/FONT]/[FONT=courier new]eno2[/FONT])
but anyway i need [FONT=courier new]enp5s0f0[/FONT] for accessing the internet and using ssh with (this is my only access path)
in my current configuration only client system on the [FONT=courier new]10.157.208.0/24[/FONT] network can see my server
I need clients on the [FONT=courier new]10.157.162.0/24[/FONT] network to be able to see it
I also need clients on the [FONT=courier new]10.130.207.0/24[/FONT] network to be able to see it
I assume I need to set the gateway on [FONT=courier new]enp5s0f1[/FONT] to [FONT=courier new]10.157.208.1[/FONT] for it to work
* This system does not handle routing on the 10.x network, it is just a static client running a basic web server on that network

here is my [FONT=courier new]/etc/network/interfaces[/FONT] file
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network (addon left)
auto enp5s0f0
iface enp5s0f0 inet static
   address 192.168.1.175
   netmask 255.255.255.0
   network 192.168.1.0
   gateway 192.168.1.1
   dns-nameservers 8.8.4.4 8.8.8.8

# secondary network (addon right)
auto enp5s0f1
iface enp5s0f1 inet static
   address 10.157.208.16
   netmask 255.255.255.0
   network 10.157.208.0

# DHCP maintenance (onboard top)
allow-hotplug eno1
iface eno1 inet dhcp

# Crossover maintenance (onboard bottom)
auto eno2
iface eno2 inet static
   address 192.168.0.1
   netmask 255.255.255.0
   network 192.168.0.0
```
Would it be a good idea to split this into 5 files in [FONT=courier new]/etc/network/interfaces.d/[/FONT]

---

### Post by pqwoerituytrueiwoq on 2017-01-29
i found some stuff
[LIST]
[*][https://www.ethode.com/blog/assigning-multiple-gateways-to-server-with-three-nics](https://www.ethode.com/blog/assigning-multiple-gateways-to-server-with-three-nics)
[*][http://linux-ip.net/html/tools-ip-route.html](http://linux-ip.net/html/tools-ip-route.html)
[/LIST]
which led me to this
[LIST]
[*][FONT=courier new]sudo ip route add 10.0.0.0/8 via 10.157.208.1 dev enp5s0f1[/FONT]
[/LIST]
i also did this to make it permanent:
```
auto enp5s0f1
iface enp5s0f1 inet static
   address 10.157.208.16
   netmask 255.255.255.0
   network 10.157.208.0
  ** post-up route add 10.0.0.0/8 via 10.157.208.1 dev enp5s0f1**

```

Is there a problem with this?

---

