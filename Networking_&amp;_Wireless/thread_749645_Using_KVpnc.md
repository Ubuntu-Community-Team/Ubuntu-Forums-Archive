---
title: "Using KVpnc"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by sk8cheez120 on 2008-04-08
So i wanted to get wireless internet to work on my laptop for school, i tried install VPN client from cisco, but i couldn't manage to install it on my laptop, So i tried using KVpnac, i got to the part where i loaded up my .pcf on to it, but now when i login try to connect it gives me an error that said:

Timeout while connecting to vpn.uvm.edu (uvmvpn) after 10s. Please check if the VPN server is reachable and the settings (UDP/TCP, local port, UDP encapsulation port) are correct. Maybe the timeout must be increased too.

What does this mean? Anyone know or how they can help?

---

### Post by cmnorton on 2008-07-03
I know nothing about Cisco connections. You'll have to play around with the configuration file. First make a copy of the original file. 

../.kde/share/config/kvpncrc

(You might have another file name. I configured pptp, but it seems like the config file name would not change.)

I launched KVpnc as root, so my file is in /root/.kde. Yours might be in your home directory.

Timeout could be several things; it's probably not something like route, but might be related to settings like mtu. Basically, you'll have to change one at a time, keeping a record of what was changed.

Also, it helps to have someone at the other end monitoring the connection. If you can take your laptop in and sit there with someone responsible for vpn, that helps, too.

---

