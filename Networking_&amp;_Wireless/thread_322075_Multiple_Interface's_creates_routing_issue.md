---
title: "Multiple Interface's creates routing issue"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by p0liX on 2006-12-19
Quick notes-
ppp0 - Dial-up to the net
wlan0 - connection to local network

Problem -
After computer is first powered on, I am able to connect to all devices on local network, once I connect to the net via dial-up, I have to manually change the default route to ppp0.  This of course breaks the local route, so I created a route for the local network to use wlan0.  

Anytime I connect ppp0 and set the default route to use ppp0 I can browse the net fine, however I can't connect to any local devices and when I attempt to ping something on teh local net i get the following message:

p0lix@zoey:~$ ping 192.168.1.51
PING 192.168.1.51 (192.168.1.51) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

I have to disconnect and reboot in order to restore the local network.  I've also tried eth0 and I get the same situation.  I also get thsi same situation when connecting to the vpn at the office using openvpn.  Anytime a second interface is enabled all other interfaces lose connection wont operate properly until I reboot.

This all worked fine in breezy badger, but once I updated I lost the functionality.

Any idea what could be causing this?  I've tried everything to get it to work and nothign I do seems to correct it.

My current route when connected to the net is below:
p0lix@zoey:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
nas59.2ar1.Leve *               255.255.255.255 UH    0      0        0 ppp0
172.16.84.0     *               255.255.255.0   U     0      0        0 vmnet8
localnet        *               255.255.255.0   U     0      0        0 wlan0
192.168.17.0    *               255.255.255.0   U     0      0        0 vmnet1
default         *               0.0.0.0         U     0      0        0 ppp0

The vmnet interfaces seem to work with no problem.  Its only with ppp0, wlan0, eth0 and tun interfaces.

Any help or guidence would be appreciated.

---

