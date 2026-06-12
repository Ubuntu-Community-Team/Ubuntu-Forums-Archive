---
title: "Wait for all &quot;auto&quot; /etc/network/interfaces to be up for network-online.target - 2min"
date: 2016-03-22
forum: Networking &amp; Wireless
---

### Post by veenarm on 2016-03-22
Hi,

I've looked and found similar topics but they look different.

I have 2 interfaces, wls1 = wireless, and ens5 = network card.

They both load/connect fine to my networks, **however** there is a 2minutes load up time saying:

Wait for all "auto" /etc/network/interfaces to be up for network-online.target [0s/2min] - waits 2 min to load, surely I can skip this somehow?
Here's my /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

auto wls1
iface wls1 inet static
address 192.168.0.201
netmask 255.255.255.0
gateway 192.168.0.1
wpa-ssid "REDWOOD_2.4"
wpa-psk "password"
dns-nameservers 8.8.8.8 192.168.0.1

auto ens5
iface ens5 inet static
address 192.168.0.202
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8 192.168.0.1

---

### Post by papibe on 2016-03-22
Hi veenarm.

Two cards on the same network? It is a very unusual configuration. Why do you want to do this?

It can be done, but you may need to set some special kernel flags. Also, you would need to set up several custom routes.

Here's some useful links: [Multiple interfaces on the same subnet]("http://pontus.ullgren.com/view/multiple_interfaces_on_the_same_subnet"), and [Two network interfaces and two IP addresses on the same subnet in Linux]("http://serverfault.com/questions/336021/two-network-interfaces-and-two-ip-addresses-on-the-same-subnet-in-linux").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by veenarm on 2016-03-23
I commented out the wifi and now it's fixed.
Not sure why adding a second would impact that bad though, as they both had explicit directives (static ips).

I had them because it's on a laptop, so when its in stationary it uses the lan, and move around wifi.

Mark as resolved!

Cheers
John

---

