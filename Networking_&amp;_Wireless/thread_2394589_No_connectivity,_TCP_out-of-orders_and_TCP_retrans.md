---
title: "No connectivity, TCP out-of-orders and TCP retransmissions with openconnect - 18.04"
date: 2018-06-18
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2018-06-18
Hi all, I haven't found anyone else with this problem so far, not sure where to start...

Brand new Dell laptop, Precision 5520, set up by my company's IT department with the 16.04 image provided by Dell, then upgraded to 18.04 and up-to-date. Wifi, networking, etc. work properly, but whenever I try to connect to the corporate VPN (Cisco AnyConnect SSL VPN) using openconnect, I don't actually get any connectivity. I ran Wireshark to see what's going on, and it seems that whenever I try to connect to anything I get a ton of TCP out of order errors and TCP retransmissions. I tried using openconnect through the command line as well as the network-manager GUI VPN connection tool, but had the same issue. I get the remote routes provided by the VPN gateway, but I can't even ping my default route on the gateway.

I'm looking for any further ideas on how to resolve. I know the VPN works with openconnect on other hardware, so it's either an 18.04 thing, or maybe something else...?

EDIT: I'm just running "sudo openconnect <name of vpn>", nothing special. This works fine on other hardware also running 18.04.

EDIT2: for giggles, I tried a USB wireless adapter instead of the built-in wifi...same issue.

Thanks!

---

