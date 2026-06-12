---
title: "Network Manager Icon Disappeared from Indicator Applets"
date: 2018-11-03
forum: Networking &amp; Wireless
---

### Post by wjbmd48 on 2018-11-03
Hi:

I'm running Lubuntu 18.04, and things were fine for a few days after install and then the Network Manager icon disappeared from the system tray.

I'm connected fine, and I can set up new connections with Preferences|Network Connections, and when I reboot I even get a transient notification telling me what network I'm connected to. 

I can even deploy the Network Status Monitor, which shows me that I'm connected, but nothing more, ie., no SSID or VPN indication.

The system tray, where the Network Manager should appear, shows, but is empty. Left click and right click does nothing. Neither does sudo service network-manager restart.

Any ideas?

Thanks!

Bill

---

### Post by wjbmd48 on 2018-11-03
Ah, I see what happened. For some reason, the indicator applets don't tile vertically, as the other applets do. I place my panel at the right margin; for some reason, the indicator applets now tile horizontally, which pushes the network manager off to the right, obscuring it, unless I widen the panel to >120 pixels, which I'd prefer not to do.

Is there a way to customize the indicator applet geometry so it tiles vertically?

Thanks!

Bill

---

