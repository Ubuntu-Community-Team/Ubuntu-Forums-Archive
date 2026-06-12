---
title: "Cant Share Desktop"
date: 2014-02-21
forum: Networking &amp; Wireless
---

### Post by mulluysavage on 2014-02-21
Machine 1: New. Running Ubuntu 12.04 Desktop. Wired connection to Linksys WRT54G v4 running Tomato v1.28. Opened Desktop Sharing Preferences. Selected Allow others to view, Allow other users to control, did not select must confirm this machine, did require user to enter password, no UPnP autoconfig, Always show notification area Icon.

Machine 2: Laptop running Ubuntu 12.04 Desktop, wifi connection to same Linksys WRT54G. Open Remmina, create new connction, entered a name for my connection selected VNC as protocol, hit connect. Returned "listening on port 5500," nothing after a couple of minutes. Fiddled around, now returns "listening on port 0" on connect attempt. Still no connection.

I don't think I'm running a firewall anywhere, not sure.

---

### Post by TheFu on 2014-02-22
I cannot help with GUI-based stuff. I know how to run remote desktops using servers without any GUI.  Sorry.

Firewalls running?  run this: **sudo iptables -L** on both platforms.

The default port for VNC is 5900-5910 ... ish, so unless you changed the defaults, that port 5500 is just ... wrong.  If you like, try to connect to port 5500 from Machine1 to machine2.

Does the server machine have a static IP? That is required.
Do these machines know each other on the network? That would happen through DNS or modifying the /etc/hosts on each.

---

