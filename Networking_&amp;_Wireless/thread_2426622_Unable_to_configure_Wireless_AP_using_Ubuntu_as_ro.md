---
title: "Unable to configure Wireless AP using Ubuntu as router"
date: 2019-09-11
forum: Networking &amp; Wireless
---

### Post by sebait9 on 2019-09-11
Hi all,
I'm trying con configure a Raspberry PI 4 with Ubuntu 18.04 as home router. My network setup is like:
                                                                                                                               
[INTERNET]--eth0/ppp0--[RPI4]--eth1--[SWITCH]---[DEVICES]

I get internet through PPPOE, configured as interface ppp0 on physical interface eth0. My ISP assigns me an IP and that works just fine, that's my WAN.
For the LAN I use a usb/ethernet dongle, named eth1. On this interface the RPI4 has static ip 192.168.1.1, runs a DNS server with PiHole and a DHCP server with isc-dhcp-server. The LAN subnet is 192.168.1/24, all configurations are done with netplan.
I configured properly ufw and all that works fine.

Now, I'd like to use the wlan0 interface of the RPI4 as an access point, binding it to the lan. Like a normal common all-in-one router. I thought to bridge it with eth1 and use hostpad for wireless configuration. Unfortunately I do not have any experience with bridges (and still not know if it is the proper way to do it). When I tryed to configure the AP, I just messed up. Several times.

Can you help me to configure that?

Thank you in advance.



P.S. sorry in case of some bad English, not my mothertongue

---

