---
title: "PPTP VPN used to work, now nothing happens"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by stefan.ohsiek on 2007-09-18
I installed VPN connection manager and set up PPTP VPN profiles and for a week it worked like a charm. Now, when I click on the network manager icon and the on my VPN connection, nothing happens. I un-installed and and re-installed both VPN connection manager and network manager with no results. Any Suggestions?

---

### Post by salamba on 2007-09-18
Have you changed to using a fixed IP on your network card recently?.   I don't think the feisty version of network manager works with static addresses.  I had to hold back the package for months after it broke just before the feisty release.  ( I'm using dhcp on gutsy now, so I'm not sure if the problem ever got fixed)

Your problem sounds exactly like what I remember having,   try switching to dhcp if you are on a fixed address.

(presuming your using the pptp plugin to network manager, or is vpn connection manager something different?)

---

### Post by stefan.ohsiek on 2007-09-18
Interesting that you mention that. I was at a customer today where I had to change to fixed IP. Only thing is that once I got back home I changed back to DHCP and now my VPN is not working

---

### Post by stefan.ohsiek on 2007-09-18
the problem (although I would rather call it a bug in network manager) seemed to be indeed because of manual configuration. I came across some interesting reading at [http://kutuma.blogspot.com/2007/05/vpn-to-windows-network-in-ubuntu.html]("http://kutuma.blogspot.com/2007/05/vpn-to-windows-network-in-ubuntu.html")

The way i solved my problem was to change all my network settings to roaming mode and then back to DHCP. believe it, my VPN is up and running again

---

### Post by salamba on 2007-09-19
Thanks for the update,  Gave it a quick try here on gutsy.  Problem still as you describe,  fortunately your fix of roaming on/off also brings things back.

Time to go looking for a bug report..

---

