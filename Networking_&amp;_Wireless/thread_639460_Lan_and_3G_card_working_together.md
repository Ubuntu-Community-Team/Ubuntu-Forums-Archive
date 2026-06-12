---
title: "Lan and 3G card working together"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by HFale on 2007-12-13
Hi there

I am new to ubuntu and I using the gutsy version in a IBM Z60m.

At this point I think everthing almost configured. I'm suck now because I dont know how (and think that it is possible)  to have my computer using the lan in my work and the 3G card all together.

And you may ask why?

Well because I need to access to the various servers when connect via Lan at work and I need access to the internet via 3G card.

At this moment I can work and use Lan and the 3G card but one of each time and not simultaneous.

My /etc/network/interfaces :

auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
    bridge_ports eth0

auto ppp0
iface ppp0 inet ppp
provider ppp0

auto eth0
iface eth0 inet static
address 10.19.1.1
netmask 255.255.0.0
gateway 10.19.100.254


Thanks in advance.

Hugo Falé

---

### Post by jcostom on 2007-12-13
> **HFale said:**
> 
Well because I need to access to the various servers when connect via Lan at work and I need access to the internet via 3G card.

At this moment I can work and use Lan and the 3G card but one of each time and not simultaneous.

My /etc/network/interfaces :

auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
    bridge_ports eth0

auto ppp0
iface ppp0 inet ppp
provider ppp0

auto eth0
iface eth0 inet static
address 10.19.1.1
netmask 255.255.0.0
gateway 10.19.100.254


What's the purpose of the bridge interface?  Typically, when one defines a bridge, the physical interfaces are not numbered, but rather the bridge interface is.

Your problem is routing related.  You've got a default gateway of 10.19.100.254, on the LAN.  That's why your system is trying to send all traffic on the ethernet, and not bothering with your wwan card.

Dump the gateway from eth0, allow the ppp link from the wwan card to set the default gateway, and if need be, add static routes to support any local networks other than 10.19/16 on your ethernet.

---

### Post by HFale on 2007-12-14
Hi jcostom

The bridge interface is related to virtualbox.

I changed eth0 to:

auto eth0
iface eth0 inet dhcp (no longer static)

but I dont understand the part - "allow the ppp link from the wwan card to set the default gateway, and if need be, add static routes to support any local networks other than 10.19/16 on your ethernet."

Is this right? Is this a static route if I put in the end of /etc/network/interfaces:
up route add -net 10.77.0.0 netmask 255.255.0.0 gw 10.19.100.254 dev eth0 (or in my case dev br0)

---

### Post by jcostom on 2007-12-22
> **HFale said:**
> Hi jcostom

The bridge interface is related to virtualbox.

I changed eth0 to:

auto eth0
iface eth0 inet dhcp (no longer static)

but I dont understand the part - "allow the ppp link from the wwan card to set the default gateway, and if need be, add static routes to support any local networks other than 10.19/16 on your ethernet."

Is this right? Is this a static route if I put in the end of /etc/network/interfaces:
up route add -net 10.77.0.0 netmask 255.255.0.0 gw 10.19.100.254 dev eth0 (or in my case dev br0)

You said you access the Internet via the WWAN card, and not over the local lan.  Therefore, just stop setting a default gateway on the ethernet card.  You don't have to do DHCP, you can stay static, just get rid of the "gateway" line.

So, you could have:

auto eth0
iface eth0 inet static
  address 10.19.1.1
  netmask 255.255.0.0
  up ip route add 10.77.0.0/16 via 10.19.100.254 (or your syntax would work as well)

But I don't know how your bridge configuration is actually working correctly...

According to this page:

[http://www.virtualbox.org/wiki/Automatic_Bridge_Ubuntu](http://www.virtualbox.org/wiki/Automatic_Bridge_Ubuntu)

Your route add syntax shouldn't be a problem, though you may find using "ip" to have a much simpler syntax.

You should be configuring the IP info on the br0 interface, rather than the physical port.  This would leave you with:

auto lo
iface lo inet loopback

auto br0
iface br0 inet static
  bridge_ports eth0
  address 10.19.1.1
  netmask 255.255.0.0
  up ip route add 10.77.0.0/16 via 10.19.100.254
  down ip route del 10.77.0.0/16 via 10.19.100.254

auto eth0
iface eth0 inet manual

auto ppp0
iface ppp0 inet ppp
provider ppp0

---

