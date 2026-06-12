---
title: "Sharing connections to a static IP"
date: 2017-04-04
forum: Networking &amp; Wireless
---

### Post by chiltz6401 on 2017-04-04
Hello Ubuntu,
In an attempt to set up an XB1 VPN I tried sharing connections with my Xbox. I ran an ethernet cable from my laptop to my Xbox, and changed the ethernet adapter so that it shared the connection with other computers. It did not work until I changed my IP settings to automatic on my Xbox. I cannot use automatic IP settings because I need my ports forwarded to a static IP for my Xbox. Without them configured, I have a strict NAT. Is there any way to share my connection to my Xbox while it has a static IP?

---

### Post by TheFu on 2017-04-04
"Any way?"

Use a router and setup the VPN on the router? This assumes you want all devices to use the VPN and the VPN supports a normal connection, like openvpn.

Setup [DHCP reservations]("http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management") for all your internal devices (or just the xbox), so you can forward ports just to that specific device. This is pretty common.  I use dhcp reservations for all my non-server devices - including network TV tuners. Why?  It makes life easier when all the devices on the home LAN have known IPs.

You'll probably want a more normal piece of hardware for the router, however.  Something that can run a normal Linux distro or pfSense - perhaps an APU2 device.  Ars Tech...a has a quick article on how to use ubuntu server for a router - which isn't bad. This allows constant patching, which solves a huge issue with almost every commercial router made - slow or no patching from the vendors.  Basically, if the router software doesn't get patches every quarter, then it isn't being properly maintained.

Clear as mud?

---

