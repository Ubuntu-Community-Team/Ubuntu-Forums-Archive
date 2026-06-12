---
title: "Setting up VPN"
date: 2014-11-23
forum: Networking &amp; Wireless
---

### Post by darkforcesjedi on 2014-11-23
I recently subscribed to an anonymous VPN service as part of an effort to shield myself from all the tracking that goes on by online service providers and advertisers. I am having difficulty though.

I set up the VPN connection using the Network Manager applet and I can connect to the VPN. But when I am connected to the VPN I can not access any of the services on my Linux machine from outside of my LAN.

Normally I can SSH into my computer from other locations. When I cam connected to the VPN I can only SSH into it from other computers on the same LAN subnet (192.168.2.x). How can I configure it to allow SSH to connect while the VPN is active?

---

### Post by darkforcesjedi on 2014-11-24
It seems this thread probably has the answer to what I am looking for but I am not sure I understand what it is doing.

[https://forums.openvpn.net/topic7163-15.html](https://forums.openvpn.net/topic7163-15.html)

There are several posts there proposing solutions and one of them says all I should need is to do this:

ip rule add from <internal IP of SSH server/VPN client> table 10
ip route add default via <internal IP of gateway/router> table 10

I don't want to just type it in because if it doesn't work I won't know how to undo it :(.

---

### Post by darkforcesjedi on 2014-11-25
For the record that seems to have worked. I can SSH into my server and it doesn't try to go over the VPN. Plex.tv (plexmediaserver) doesn't seem to work from over the internet though. Still trying to figure that one out.

---

