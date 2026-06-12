---
title: "linux router issues"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by piccard on 2005-09-04
My hardware setup is as follows: a ubuntu box running a gnome gui.  I have a connection from my dorm room ethernet port to the onboard NIC of the 'nix box.  I then have a USB200M linksys ethernet adapter that has a line running from it to a gigaswitch (d-link).  Then, from the giga switch to the other clients, at the moment just a windows machine. I'm trying to use firestarter to configure the router/firewall.  

When I start firestarter, it gives me an error 'unable to start firewall, unknown error'.  however, the firewall still works and is actively blocking connections from the WAN, and I can route just fine.  my eth1 (WAN) and eth0 (LAN) are both enabled in the network configuration of ubuntu.  eth1 is set to DHCP, and eth0 is set to static.  I have firestarter set to use dhcp for the internet connection sharing, but my windows machine refuses to pull an IP.  Any suggestions?

---

