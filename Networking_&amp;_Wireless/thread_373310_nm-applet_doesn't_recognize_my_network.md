---
title: "nm-applet doesn't recognize my network"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by El_Matthews on 2007-03-01
Gents

the nm-applet always says I have no connection even if I am surfing and copying files to my server.

where does the nm-applet gets its config from ? it always says eth0 not connected.

PS: I use a static IP in my network

---

### Post by joekepley on 2007-03-01
NetworkManager only manages network devices that aren't otherwise configured in /etc/network/interfaces. So if you have a static IP configured, then NetworkManager will ignore that interface so it doesn't go around messing with your static IP. 

In the case of a static IP, NetworkManager isn't of much use, since there's nothing to 'manage'. Its real utility comes in situations like a laptop, where it might be either plugged in to a wired LAN or drift among multiple wireless connections. The only thing NetworkManager might be of help to you with would be setting up VPN connections. 

You might want to use Network Monitor instead (right-click the panel, select 'Add to Panel...', choose Network Monitor). That will show you network activity without trying to manage your connection, which doesn't need managed since it's static.

Hope that's useful.

---

### Post by El_Matthews on 2007-03-05
thanks, tread can be closed

---

