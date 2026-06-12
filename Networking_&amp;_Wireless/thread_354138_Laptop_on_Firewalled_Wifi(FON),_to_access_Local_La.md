---
title: "Laptop on Firewalled Wifi(FON), to access Local Lan, (VPN I guess)"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by eldaria on 2007-02-05
Hello people.

I have a small network at home consiting of the following.

An ADSL router handling access to Internet, Firewall, DHCP and routing to internet for the local network.
Connected to the router are 2 devices.
A Fon, Fonera Wireless Router. [http://www.fon.com]("http://www.fon.com")
A simple 8 port Switch.

On the Switch are permanently 3 Computes connected. 
PC with Ubuntu Server, serving as HTTP, SMTP, IMAP, NFS server.
PC with Kubuntu Desktop
PC with Windows XP Desktop

Also on network is a Kubuntu Laptop, that mostly runs Wireless on the Fonera Router, but sometimes on the switch by wired Ethernet.


So to my problem.
On my server I'm running a couple of domains.
When i try to connect with a browser to any of these domains from a wired connection, there are no issues, the website comes up and everything is great.
However when using the wireless network, i get the login of my router.
When I type in the IP address of the server it connects to the server but tells me that I need to use the domain to connect and not the IP.

So i tried some DNS lookup.
From Wired PC to my Domain will give me the Local LAN IP as configured on the ADSL Router.
But from the Wireless It gives me my External IP, as if I was on the internet.

So I guess my Fon router is looking up DNS externally for internal LAN Devices.
Since I'm not able to configure the DNS on the FON router, my next though was to set up some kind of VPN on the server and Laptop, and then connect over the wireless to the LAN so that the laptop thinks it is on the local LAN and get's configured as such.

But I have no clue on how to do this, or perhaps someone else has a better idea?

Regards.
Brian.

---

