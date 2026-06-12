---
title: "Strange Network"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by rrrobles on 2008-01-19
I have the following scenario:

* Two computers plugged into a hub.
* A *bridge* ADSL modem plugged in the same hub.

I want to share the net connection to the two computers.
In this scenario I'm able to connect to the modem with both the computers, but it is a *bridge only* modem, so I can connect only one computer at a time.
My ideia is connect in one computer and configure the second computer to use the first as gateway.
It should be simple, but the computers refuse to see each other.

The first computer is configured as static ip 192.168.0.1. etc/network/interfaces:

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0

The second is configured as static ip 192.168.0.2 as follows:

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

The physical connections are ok, because I can reach the bridge modem by the two computers.
The interfaces is up seen by ifconfig.

But if I try to ping one computer by the other, I get no response.

Anyone can see any clue?

---

### Post by jonallport on 2008-01-19
All I can suggest is NAt, don't bridge

---

