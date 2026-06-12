---
title: "VPN using Windows and/or Cisco/Linksys"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by TorchlightJay on 2007-11-10
Okay, so I want to get one of those Linksys routers that come with VPN features. I am pretty confident with my setup on the router. How would i connect using a Linux computer? What applications would I need and what other programs would I need? Also, Let's say I had a traditional Windows PPTP server for VPN and wanted to connect. All Windows machines connect fine, how do I get my Linux machine to connect? Thanks all.

---

### Post by TorchlightJay on 2007-11-12
any ideas anyone?

---

### Post by plehman on 2007-11-13
I don't think I have all the answers you're looking for, but on my Ubuntu laptop (7.10), I was able to get a vpn working to my office (managed by a Cisco ASA firewall appliance) by using the Syanptics Package Manager to install the following items:

network-manager-vpnc
vpnc

Installing these and whatever required packages they had resulted in an added a VPN Connections menu item to the Network Manager where I could then enter the details of my VPN connection.

That way, once I had a network connection, I could go to the menu item and select the vpn connection I wanted and connect.  Hope that makes sense...

Also I noticed that the Package Manager has programs available for PPTP (pptpd, etc.)  but since I've never used them, I don't know if they are exactly what you are looking for.

Good Luck.

---

### Post by rimoth on 2007-11-13
Havn't done this yet with Gutsy, but for Feisty also used vpnc & then connected and disconnected via the terminal window as could not find a Gui to support it

---

### Post by knowledge_is_power on 2007-11-13
i downloaded vpnc to connect to my campus' cisco vpn, and theres a GUI frontend out there called KVpnc that supports PPTP as well, as long as you have the backend installed.

---

### Post by marusiraa on 2007-11-15
can someone post the site where you can download vpnc or the cisco vpn client for linux please.

Thanks

---

