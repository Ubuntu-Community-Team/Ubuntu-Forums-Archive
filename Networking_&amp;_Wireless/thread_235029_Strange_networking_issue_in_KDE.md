---
title: "Strange networking issue in KDE"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by Psquared on 2006-08-12
I was using Kopete last night and when I went to bed I logged off and this morning when I logged on I had no internet. The funny thing is that its only in KDE. When I boot into Gnome (separate partitions) networking is fine.

lspci shows the network "lo" and eth0 are recognized.

however, i can't ping anything except my router which loops endlessly. I did install some software to try and get my camera working "digiKam" but the internet was working after that.

What could be different about the KDE network/internet setup from Ubuntu-Gnome? Is KDE just flaky this way?

This is a wired ethernet connected to a Linksys router. The wireless part works great and its not the NIC because as I said the same system works fine in Gnome. So whatever it is is KDE specific.

Anybody got any ideas?

Thanks

---

### Post by Psquared on 2006-08-12
Well, i fixed it. The dangest thing. I had installed the firewall guarddog and clamav. Along with some things to make my digital camera work. I uninstalled all that and then went into network settings and saw that my eth0 was disabled. I enabled but still got no internet. I went into advanced settings and changed dhcp to fixed and then rebooted. Now its up and running. 

Why would KDE require those settings while Gnome uses DHCP??:confused:

---

