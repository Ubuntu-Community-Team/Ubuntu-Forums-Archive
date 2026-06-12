---
title: "Accessing networked drive through openVPN"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by Scynet on 2008-03-29
Hello,

I have a Dell Latitude D630 with Vista and Gutsy installed on their own partitions. I use OpenVPN to connect to my school's network drive (Z:, each student has a part of this drive at his disposal). I have certificates and openvpn configuration files with which I can connect just fine from Windows. However, I can't seem to get it working right from Ubuntu. I'm a bit of a newbie with OpenVPN so I can't really even troubleshoot the problem properly. What I do know is that starting openvpn client from terminal doesn't give problem but won't give any access either. Using network-manager-openvpn, however, gives me an error after a while, and no connection at all:

"VPN Connect Failure.
Could not start the VPN connection '<name>' due to a connection error.
The VPN login failed because the VPN program could not connect to the VPN server."

The certificates and config files are the same that I use in Vista, but Ubuntu can't connect with them. This might be some sort of routing problem (I have a router at home, but this error occurs when not using a router too). Any ideas?

Note: School uses a Windows network.

---

