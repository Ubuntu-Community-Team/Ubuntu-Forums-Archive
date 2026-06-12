---
title: "Connecting device directly via Ethernet"
date: 2018-01-14
forum: Networking &amp; Wireless
---

### Post by rowan2 on 2018-01-14
I'm trying to connect a device (HDHomerun TV Tuner) directly (no switch/hub) to a PC using Ethernet. The PC's Wi-Fi card will provide internet access.
As far as I know, I require a DHCP server running in Ubuntu to provide an IP for the tuner on the Ethernet port.
I have tried setting this up using [COLOR=#111111][FONT=Consolas]isc-dhcp-server and editing:

[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]  /etc/default/isc-dhcp-server,[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]
  /etc/dhcp/dhcpd.conf[/FONT][/COLOR][COLOR=#111111][FONT=Consolas], and
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]  /etc/network/interfaces
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]
but I'm having trouble.
[/FONT][/COLOR]One time I had it working alright, but when I reset the PC the tuner's IP changed, and mud really hit the fan when I started trying to allocated a static IP using the tuner's MAC address.
[COLOR=#111111][FONT=Consolas]
A few questions that I believe would help me out:

1. Does editing [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]/etc/network/interfaces and configuring a static IP override the Ubuntu 17.10 GUI network settings? Which has the final say in how the network runs? Or are they both linked?
2. Do I need to bother setting up a gateway or a DNS server if I'm not accessing the internet?
3. In the [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]/etc/dhcp/dhcpd.conf, do I need to bother with DNS settings (i.e. do I even need a [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]domain-name or [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]domain-name-servers[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]?) or setting a 'router' address?, or can I leave them out of the declaration?
4. Should I declare a static IP for the tuner that is outside the normal IP range that an be allocated? I wouldn't think this would matter with one device connected.

Going forward, I would like to bridge the networks, but I can't even seem to get a completely isolated setup working.[/FONT][/COLOR]

---

### Post by TheFu on 2018-01-14
If you want to make your Linux computer behave as a router, then configure it as a router. There are 100+ how-to guides for that.  Just be aware that a router is an edge security device and that running anything else on it diminishes that security.  If you want to setup a linux-based router, forget the GUI network tools.  BTW, I wouldn't use 17.10. I'd use 16.04 for this.

I have 3 HDHR network tuners, so I understand how these things work. Mine get the same IP every boot from a local DHCP reservation.  While this isn't necessary if you only use the correct drivers for all clients, I like to record from 1 of the devices using wget. That means my recording machine needs to know the IP, which cannot change.  It also makes troubleshooting any issues easier when each device is always at the same IP.

With all that said, I think you are doing this the hard way.
Put the HDHR device on the LAN. Put the computer on the LAN. Have the LAN managed by a router which provides internet access. Cheap internet routers are $15, though they aren't exactly the best or most secure, they do work for a wired connections.

17.10 changed how networking is configured. Manually editing the interfaces file isn't used anymore. [http://www.ubuntugeek.com/disable-netplan-on-ubuntu-17-10.html](http://www.ubuntugeek.com/disable-netplan-on-ubuntu-17-10.html) The new techniques aren't documented everywhere.  This is another reason to stay with 16.04.

Which model of HDHR do you have?  I have v3 and v4 devices.

---

### Post by rowan2 on 2018-01-15
> **TheFu said:**
> If you want to make your Linux computer behave as a router, then configure it as a router. There are 100+ how-to guides for that.  Just be aware that a router is an edge security device and that running anything else on it diminishes that security.  If you want to setup a linux-based router, forget the GUI network tools.  BTW, I wouldn't use 17.10. I'd use 16.04 for this.
Cheers for the advice. I'll look into a router-type configuration tonight.

> **TheFu said:**
> With all that said, I think you are doing this the hard way.
I totally agree with this. My house is fully networked, but this is for my mother. Her rental is laid out in a very unfriendly way with respect to networking. There is a single ADSL2+ port which is nowhere near the TV and antenna port which is the whole reason for this configuration. But like you say, maybe I'm better off with a switch or Wi-Fi repeater somewhere near the HDHR.

> **TheFu said:**
> Which model of HDHR do you have?  I have v3 and v4 devices.
I'll check this for you when I get home tonight.
EDIT: It's a 'HDHR4-2DT'.

---

### Post by TheFu on 2018-01-15
HDHR needs a wired connection AND wired connection performance to be usable, IME.  Wifi isn't ever a solid connection for streaming video, especially hidef.  Wifi bandwidth, even under the best situations, is choppy.  Humans don't see how bad it is, but video streaming will show it, even with 300Mbps wifi connections.
[B]
Another option to consider[/B]
Can you use powerline networking?  If it works, it would be stable, predictable, unlike wifi.  I've tested it here with a nicely rated, 600Mbps, Zyxel powerline setup.  220Mbps in the same room.  100Mbps on the same floor, 60Mbps between different floors.  My house was built in the early 1990s, so the wiring isn't ancient. Basically, bandwidth is 10% of whatever the advertised speeds are for where anyone would deploy it.  But powerline doesn't work in all situations, especially older homes with really poor electrical wiring, so it might not be an option.

My antenna is in the attic. Coax running 30 ft to a splitter to feed multiple HDHRs. For a single connection, 30 ft shouldn't matter much, assuming it can be hidden. Just another consideration.

---

