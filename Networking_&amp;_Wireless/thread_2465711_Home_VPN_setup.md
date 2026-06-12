---
title: "Home VPN setup?"
date: 2021-08-09
forum: Networking &amp; Wireless
---

### Post by JimLS on 2021-08-09
I have been doing some reading and working thought setup but have some questions...
Have a fairly recent Asus router that has VPN built in so thought I would just use that (unless that's a poor choice...)
Internet is via ATT DSL - was upgraded to uverse several years ago - point is I found some notes on how to bridge it so the router gets the public IP.
Still unclear on how I connect to several web servers at home.  Realize I need to have software on both ends of the connection.  
Do I need to take additional security precautions?  The web servers run Linux.  They will be accessed by Android phone or Windows PC.  Should I set up fail2ban or additional security?  Up to now I haven't had any ports open so want to make sure I do what I can to make this secure.

---

### Post by TheFu on 2021-08-10
Please don't run a VPN on a router.  Routers have enough to do just with a firewall. A misconfiguration of any "extras" and the firewall settings are at risk too.  How often are all those "extras" patched?  We know with Linux desktops, there are patches every week.  I patch my router every week, though updates usually are available every other week.

So ... if you want to have personal access to websites you run at home, then using ssh, a socks5 proxy, or a full VPN are all viable solutions.  For Android, the full vpn will be easiest.  I do that to access my nextcloud, plex, Calibre, email, and wallabag servers that I self-host at home.
I don't use Windows outside the house. Just cannot trust Win10 due to the 1-sided EULA which I never agreed to.

As for VPNs, I've run openvpn, wireguard, and IPSec both at home and for clients. Wireguard is the newest and is both much easier to setup and much easier to connect from the clients you've listed. I've been running it for a few months, though I still maintain an IPSec VPN for when security is critical.  OpenVPN is based off SSL/TLS.  There are always new flaws being found in the implementation of those protocols, so beware.  Only allow TLS v1.3 or later. DO NOT USE TLS v1.2. That has been cracked.

Where should you run the VPN?  That depends. I run them in a virtual machine with a dedicated NIC just for the VPN. It is setup using IOMMU passthru so the hostOS isn't involved and my other VMs on the same system do not share the same bridge. Some would call this paranoid.

[https://blog.jdpfu.com/2011/08/21/readers-ask-about-vpns](https://blog.jdpfu.com/2011/08/21/readers-ask-about-vpns) has links to a number of articles you might find informative. Check out the Reverse Proxy one so you can access different internal websites, though with a properly configured VPN, you won't actually need a reverse proxy.  I use mine as a TLS termination point for all my websites - internal and external.

ssh should always have fail2ban, but that is not sufficient security. Never use passwords for authentication over the internet.

I wouldn't run any VPN on a router either, if that wasn't clear.  WAN Routers need to be dedicated devices running on real hardware.  LAN routers can be virtualized, if you like. That's more flexible and if someone is inside your LAN already, they can probably figure out how to crack a local root account and setup routing between different subnets anyways.

---

