---
title: "VLAN routes on RaspberryPi ubuntu"
date: 2017-02-26
forum: Networking &amp; Wireless
---

### Post by patricrpi on 2017-02-26
Dear experts

I am a bit puzzled and my internet research has not been successful. I have set up a RaspberryPi with 4 VLAN interfaces and I am wondering about the route table.

In my understanding both entries for Iface eth0 are not needed (or even confusing?). From examples I found in forums I understand that I need to bring up eth0 although I only want VLAN communication, right?

At the moment eth0 is configure as manual with no IP address. All VLAN interfaces are configured with static IP addresses.

Why are 2 default gateways shown? And what is link-local?

[COLOR=#000000][FONT=Menlo]Kernel IP routing table[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]default         10.10.130.1     0.0.0.0         UG    0      0        0 eth0.130[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]default         *               0.0.0.0         U     1002   0        0 eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]10.10.110.0     *               255.255.255.0   U     0      0        0 eth0.110[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]10.10.130.0     *               255.255.255.0   U     0      0        0 eth0.130[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]10.10.210.0     *               255.255.255.0   U     0      0        0 eth0.210[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]10.10.230.0     *               255.255.255.0   U     0      0        0 eth0.230[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]link-local      *               255.255.0.0     U     0      0        0 eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]link-local      *               255.255.0.0     U     1000   0        0 eth0.130[/FONT][/COLOR]

I can access the RaspberryPi from VLAN 110 on its VLAN 110 IP address but not on its VLAN 130 IP address. Firewall rule seem to be fine.

Thank you, Patric

---

