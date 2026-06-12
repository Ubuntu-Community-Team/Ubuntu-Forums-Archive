---
title: "Selective use of VPN Tunnel"
date: 2014-11-22
forum: Networking &amp; Wireless
---

### Post by joerg_ac on 2014-11-22
Hi,

I am considering a VPN service where the Ubuntu machine is the endpoint. I am running Ubuntu 14.10 with all the latest updates.
The problem is that to my understanding all traffic will go through the VPN tunnel by default (I consider either PPTP ort OpenVPN). 

The problem is that I have services on that machine like Apache for my own website, SFTP server, which I also access from the WAN, SAMBA, that provides shares in the LAN (no WAN access is wanted for these shares. I have SFTP for remote access). Furthermore I use BTsync to automatically share files between my mobile devices. To make some of this work I have my router using DynDNS and my own domain name. For the future I plan to also add my own mail-server and there is also a PLEX media server that I access from mobile devices.
I would like top keep all traffic from these services out of the VPN tunnel and access the network directly.

The only services that shall use the tunnel are firefox and transmission.

The peoblem is therefore that I use the same machine as server for several services and at the same time as client for accessing the internet. I would like all server tasks accessing the network directly, while traffic for web-browsing and P2P shall go through the tunnel. this would be relatively easy to set up if I could bind applications to network interfaces, but that seems to be not possible, right?

The machine has only one physical ethernet device, but it is of course not a great deal to create a virtual interface and getting a second IP address from the router it that helps. 

I also understand that I can use iptables to filter out traffic that is not supposed to go out on a particular interface.

I guess I need to setup routes, but that is IP based and not based on originating/destination application of the application.

Does anybody has an idea how to setup routing on the ubuntu machine to distingush the traffic accordingly?
I want ot have only Web browsing and P2P (torrent) traffic throuth the VPN. Some pointers would be highly appreciated.

Best regards, Joerg

---

