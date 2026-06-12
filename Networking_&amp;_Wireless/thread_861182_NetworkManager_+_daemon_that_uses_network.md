---
title: "NetworkManager + daemon that uses network"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by perrce on 2008-07-16
I've been trying to install a daemon that looks for a local IP address when it starts. It works fine if I start it from the command line after logged into Gnome, but when I start it through /etc/init.d at boot time it fails. Through the magic of open source, I was able to put in some debug messages, and discovered that the problem seems to be that it can't find an IP address when the daemon is started at boot time. 

I'm running on a laptop (no ethernet in use) and use Network Manager to control my wireless network interface. I'm guessing that my problem is due to the fact that my daemon is starting before I log into gnome. Since I'm not in gnome when the daemon starts, Network Manager hasn't yet grabbed an IP address via DHCP. Problem is, I don't know enough about Network Manager to know if that makes sense.

So the questions are: If I'm using Network Manager is there no IP addresses assigned until I log into Gnome? Is there any way to have Network Manager grab an address earlier?

---

