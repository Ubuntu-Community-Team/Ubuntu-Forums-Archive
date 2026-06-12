---
title: "VPN setup on Netgear Nighthawk router"
date: 2019-11-10
forum: Networking &amp; Wireless
---

### Post by DawgMan on 2019-11-10
I just moved to a new location and my ISP (Mediacom) does not support VPN.  So I got a new router a Netgear Nighthawk R7000.  The Media tech support "baselined" their modem (ie turned of routing).  I have turned on the VPN on the R7000 and still get the "The VPN connection disconnected because the VPN service stopped".

I have installed openvpn "sudo apt-get install openvpn" and "sudo apt-get install network-manager-openvpn"

I downloaded the config files from netgear and put them in /home/{user}/vpn folder.
ca.crt, client.crt, client.key, and client2.conf

The site I was following said to copy the OpenVPN configuration file (e.g. vpn1234B_1.ovpn) to the installation directory. There is no .ovpn file and I can't find one anywhere.  The onlything in the /etc/openvpn directory is update-resolv-con.

I'm trying to connect to my work computer from home.  If I use my cell phone as a hotspot it works fine so I know my settings are correct.

I tried portforwarding 1173 and nothing.

I am on 16.04. 

Any help would be appreciated.

-DG

---

