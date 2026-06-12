---
title: "Need help with PPTP VPN"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by rjr162 on 2008-10-16
I'm trying to setup a PPTP VPN link between my laptop with ubuntu 8.10 and my dd-wrt router.

I have PPTP daemon enabled on the router, and setup as best I could figure out, but no go.

Server settings:

Server IP: 192.168.1.1 (which is the router IP per the HELP button, but also tried the DYNDNS addy I have) 

Client IP(s): 192.168.0.200-205 (put that in after trying 192.168.1.200-205 but no luck with that either)

I'm using Ubuntu 8.10 and installed PPTP, OpenVPN, and CVPN in an attempt to get something to go.

So I find a random wireless router and connect. I can get online etc etc. I then click the wireless manager and enable the VPN connection. It connects, logs in, and that's that.

When you type "ifconfig" in a terminal window it shows the following connections:

eth0, wlan1, PPTP0, and one other I can't remember. But you can't go anywhere online. It just sits there "waiting for xxxx" or "connecting to xxxx" in firefox. Disable the VPN and it everything works fine.

---

