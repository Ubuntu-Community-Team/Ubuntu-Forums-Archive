---
title: "network problem with Intel Pro100"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by skep on 2007-04-21
Hello!

I have a network problem under Xubuntu Feisty Fawn with my T23 laptop.
This is my setup:

DSL-Modem (external) ---> Router (WRT54G) --> Laptop

The problem is, that I can't get the internet to work (no ping, dhcp ect.).

ifconfig shows 3 devioces:
eth0:
with no inet address

eth0:avah
inet address: 169.254.5.137
Bcast: 169.254.255.255
mask: 255.255.0.0

lo:
loopback device

lcpci shows the network card as:
Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) EthernetController (re 42)

lsmod shows the following modules:
e100
eepro100

In my network setting i have enabled interface eth0 with automatic configuration (DHCP).

Nethertheless ping gives me nothing and ifup or /etc/init.d/networking restart shows:
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval x (x = 7,11,13 ect.)
No DHCPOFFERS received.

I can't even ping the router:
ping 192.168.1.1
From 169.254.5.137 icmp_seq=x Detination Host Unreachable

Can anyone give me a hint on what I'm doing wrong?

---

### Post by skep on 2007-04-21
Problem fixed:

I use now a static configuration in my etc/network/interfaces (no dhcp) and this seems to work just fine..

---

