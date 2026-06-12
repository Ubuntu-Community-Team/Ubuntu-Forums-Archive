---
title: "One static IP network and DHCP networks"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by rodje on 2008-01-03
I have clients who need to connect to one network which is static IP and static dns settings over ethernet and also to DHCP networks over wireless.

I'm looking for the easiest way to allow people to manage this. When the user is connected to the ethernet network I'd like their wireless card to be disabled also.

One way to do this is via NetworkManager locations which is cumbersome and requires root.
One way is perhaps to write 2 scripts which the user could click on to change settings e.g. "Static IP script", "DHCP".

Is there an easier way to do this?

---

### Post by Predator[23rd] on 2008-01-03
Hi!

You can assign mutliple configurations to a network interface card in */etc/network/interfaces* by having (example):
[I]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth0:1
iface eth0:1 inet static
 address 192.168.1.10
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 gateway 192.168.1.1

auto wlan0
iface wlan0 inet dhcp[/I]

why is there a need to disable an unused NIC?

---

### Post by rodje on 2008-01-03
Hiya, I've noticed that when I connect to the wired network both interfaces remain active which doesn't sound like a good idea?

If you do what you suggest how does the network interface "know" which eth0 config should be used?

---

### Post by Predator[23rd] on 2008-01-03
an active but unused network interface can be safely ignored.

check these for IP ALIASING:

[http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html](http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html)

[http://www.faqs.org/docs/Linux-mini/IP-Alias.html](http://www.faqs.org/docs/Linux-mini/IP-Alias.html)

your OS will try all interfaces until it finds one which does whatever it needs...

---

