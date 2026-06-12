---
title: "Feisty Openvpn Client: tap adapter doesn't shut down completely"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by puyi on 2007-04-25
I've  been fighting with my linux client setup for OpenVPN for a few months now. In brief, I'm using Linux routers with dd-wrt firmware with OpenVPN embedded. Using the OpenVPN how-to I have a working network with one router as server and two client routers, bridged mode, Certificates with 2048 encryption. I have no problem with my road warrior Windows clients using OpenVPN Gui client.

In Linux clients I believe dhcp doesn't work. Previously in Dapper and now in Feisty I set static addresses in my client.conf file with added script "ifconfig <IP address> <Subnet Mask>" to successfully connect to my network.

My problem is when I exit OpenVPN in the Terminal with CTRL+C command the virtual tap adapter for the session doesn't shut down completely. When I login OR restart, Ubuntu maintains the ghost of the adapter from the previous session so that when I initiate OpenVPN in the Terminal again, ANOTHER tap adapter is created with the same ip and subnet and thus OpenVPN FAILS.

My current workaround requires I remove the client.conf file from /etc/openvpn at shutdown or logoff, then copy the working client.conf (which I saved to my home directory) the next time I need to VPN into my network. This is a real PITA. :( 

Is there a way to bring the tap adapter down manually?

---

