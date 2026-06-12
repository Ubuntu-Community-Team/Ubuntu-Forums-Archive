---
title: "Wireless Client Bridging"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by khalis on 2008-08-13
My home network setup is less than optimal and I'll quickly explain:

Cable modem is upstairs connected to a WRT54g v2.0 running dd-wrt v24.  It uses WPA2.  Downstairs is a WRT54g v6.0 working as a Repeater Bridge.  Finally, inside my room I have an old Acer laptop running Ubuntu 8.04 Server wirelessly connected to the basement wireless.

The problem I'm having is the wireless signal directly from upstairs to my room is too weak to be reliable, so I have the second device set up repeating halfway between me and the upstairs router.  In order to connect wired devices in my room to the wireless I want to bridge the wireless and wired interfaces on the Acer to add them to the same subnet as the rest of the devices in use.  My attempts so far haven't worked.

Wired interface: eth0
Wireless interface: eth1

What I've tried so far:

brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1
brctl stp br0 off
ifconfig eth0 0.0.0.0 up
ifconfig eth1 0.0.0.0 up
ifconfig br0 192.168.1.10 subnet 255.255.255.0 up
route add default gw 192.168.1.1

This doesn't work at all.  All packets in every direction are dropped.  iwconfig shows that I have a stable connection to the basement AP every time I check.

When I remove the wired device from the bridge, everything starts working, though.  (brctl delif br0 eth0)  I can use dhclient on br0 to get an IP, ping other clients/internet, etc.  As soon as I add eth0, everything fails.

Any suggestions about what's going on or am I doing something wrong in the bridge setup?  I've used bridging before with OpenVPN and everything seemed to work fine there, but this is a little beyond the norm for me.

---

### Post by khalis on 2008-09-21
Well, after giving up on this, I've learned that it is most likely because the wireless driver does not support bridging and so I cannot do what I want without using a NAT/router.

---

