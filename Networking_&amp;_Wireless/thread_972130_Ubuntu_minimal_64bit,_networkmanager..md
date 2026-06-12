---
title: "Ubuntu minimal 64bit, networkmanager."
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by bredin on 2008-11-05
Just installed ubuntu 8.10 64bit minimal. Running XFCE4 and want to use my wificard ( intel 4965AGN ). 
I've installed the network-manager-gnome package. But I can't start nm-applet. I've added nm-applet to autostart in xfce4 but it does not start. And when I boot the computer it configures the network before it starts the networkmanager. So it's probably a conflict there. 

The wificard should work, becuse I can find my wifi-network using wifi-radar. 

In archlinux I had to replace the network module with the networkmanager module in the /etc/rc.conf file to make it work. But there is no rc.conf file :confused:. How do I do it in ubuntu? I want to remove the module or whatever it is that configures my network before networkmanager.

---

