---
title: "How to make a network from a wireless connection?"
date: 2015-06-09
forum: Networking &amp; Wireless
---

### Post by vayu on 2015-06-09
My desktop connects to the internet with wifi on a verizon cable setup/router which I don't have direct access to except the wireless ssid and password.

I shared my wireless connection through the wired connection to another computer using network manager.  I want to do the same thing except instead of sharing it to one computer I want to share it to a router which then has it's own whole newtork.  Network Manager has several connection types that look interesting but I have no idea what they mean.  Do I want to set up a VPN, am I wanting a bridge, or am I just wanting to share to other computers?  Once I know what type of connection, I need to know how to fill in the settings, like IP adn gateway....  Am I on the right track?

---

### Post by ian-weisser on 2015-06-12
Network Manager icon --> Edit Connections

Wireless Connection: Change nothing. Don't touch it.

Wired Connection --> Edit --> IPv4 Settings Tab --> Method: --> Shared to other computers

Don't touch any other settings. Network Manager will automatically create a new network on the eth connection, start it's own DHCP server for the new network, and connect the wired and wireless networks.

---

### Post by vayu on 2015-06-13
Thanks. It's working great.  Any idea how I might tell it what IP to give out?  It currently sets its IP to 10.42.0.1, and I want it in the 192.168.x.x range.

---

### Post by ian-weisser on 2015-06-13
The short (but usually unsatisfying) answer is to create a config file for dnsmasq. See /usr/share/doc/dnsmasq-base/examples/dnsmasq.conf.example

The longer explanation of why the answer is unsatisfying, and why there is no trivial way to do what you ask, is that you are connecting two separate networks that use two different DNS servers. The IP addresses of each network *should* be different and non-conflicting.

---

