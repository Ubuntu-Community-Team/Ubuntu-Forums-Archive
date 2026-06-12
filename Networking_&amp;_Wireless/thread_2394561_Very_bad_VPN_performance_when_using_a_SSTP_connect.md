---
title: "Very bad VPN performance when using a SSTP connection"
date: 2018-06-18
forum: Networking &amp; Wireless
---

### Post by trax-xavier on 2018-06-18
Hi,

I have a problem with my Ubuntu 18.04 (with installed KDE desktop),
I have to connect to a windows 2008 R2 VPN serve over SSTP, and this does not work properly.

First it was not quite obvious how to get it to even connect, as apparently the KDE desktop allows me to create a SSTP VPN connection but when I try to connect it says the required client is missing and apparently no default repository has one :/

After some googling I found this:
sudo add-apt-repository ppa:eivnaes/network-manager-sstp
sudo apt-get update
sudo apt-get install network-manager-sstp
sudo apt-get install sstp-client

I have set up the VPN to only route traffic for my home sub-net so that me surfing the internet does not take a unnecessary detour.

With it I can connect to my SSTP server, however the performance is really really bad, when using RealVNC to access the server the speed with which the screen is updates at the high color setting is unbearable, while connecting directly without the VPN works just fine. Looking on the network graph of the System Monitor its roughly 1/4th of he speed going through the VPN in comparison to a direct connection.
Also accessing samba shares on the server gives me data rates of a few 10 kb/s, while my home server has 30 MBit upload!

Booting the same machine int windows 7 and going into the SSTP VPN works just fine, the transfer speeds are what one would expect given the available upstream and working remotely with VNC feels almost like being in front of the actual PC.


So what can be the problem here?
Did I pick the wrong sstp-client? Are there better clients to be installed?
I tried to test a PPtP connection but for some reason my university (that is from where I access my home network) seam to block PPtP traffic, does not work with win 7 eider.

So how can he issue with the SSTP performance be fixed?
Or what other options do I have to access a Windows 2008 R2 VPN with decent performance when using Ubuntu 18.04 as client?

Any help would be very helpful :D

Cheers
Trax

---

### Post by trax-xavier on 2018-06-19
After some failed attempts to get L2TP/IPSEC to work, I have set up openVPN on my windows box, with it using TCP the performance was just as bad as with the SSTP, how ever when I switched to UDP it started working properly.
Ok, TCP over TCP may not be the best idea, but windows gets it to work, so why not ubuntu?!

The problem with a openVPN server on a windows based router is that through this VPN I can only access the router but not the rest of the LAN :/ or at least not easily, I will have to mess around with the ras and routing service may be there is a way to get it to work.

But the question remains? is there any way to get SSTP VPN to work on Linux with the same performance as it does on Windows?

---

