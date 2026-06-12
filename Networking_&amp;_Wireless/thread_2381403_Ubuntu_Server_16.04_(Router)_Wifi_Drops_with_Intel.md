---
title: "Ubuntu Server 16.04 (Router) Wifi Drops with Intel 3168"
date: 2017-12-30
forum: Networking &amp; Wireless
---

### Post by tehsharkness on 2017-12-30
I've been reading a ton of similar posts to mine, but I haven't had any success with the changes I've made so far. I've been attempting to setup a router running Ubuntu Server 16.04, but the wifi drops seemingly at random. Here's a picture of my current network setup:
[IMG]https://i.imgur.com/F3uJ6lo.png[/IMG]

Everything from Mountain View RV up is not managed by me, so if it ends up being that the wifi is just unstable, so be it. I'm just trying to eliminate any instability in my own network, and learning about Ubuntu as I go along.

Anyways, as you can see from the diagram above, I have my router using it's Intel 3168 WiFi adapter acting as the WAN port and one of its 2 Ethernet NICs acting as a LAN port. The router is also the primary (and only) DNS and DHCP server for my LAN. The WLAN port receives a DHCP address from the WAP above it.

I've run the standard wireless-info script I've seen in countless other threads here, and linked it here: [URL="https://paste.ubuntu.com/26288078/"]https://paste.ubuntu.com/26288078/

[/URL]For a broad overview of what I've tried so far, I've tried various iwlwifi options, such as turning off 802.11n functionality, disabling Bluetooth coexistance, disabling power-saving mode, etc.

After discovering that the iwlwifi driver was not looking to load the most current (as I understand it) 3168 firmware, I updated the driver (via updating the Linux kernel).

For the setup of interfaces, iptables, dhcp, and dns I followed along with 2 different tutorials:
[https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch)
[https://killtacknine.com/building-an-ubuntu-16-04-router-part-1-network-interfaces/](https://killtacknine.com/building-an-ubuntu-16-04-router-part-1-network-interfaces/)

The hardware itself is a custom build. ASRock MB with an Intel Celeron processor are the 2 main components. Side-note: ASRock materials claim the WiFi adapter on-board is a 3160, but Ubuntu detects it as a 3168. Grrrr.

---

