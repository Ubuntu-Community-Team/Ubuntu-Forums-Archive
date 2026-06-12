---
title: "Network Manager does not remember my settings"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by Johan_SV on 2007-03-26
Hey,

I have installed network-manager and network-manager-gnome today, as it looks like it is a handy tool to work with wireless networks when you don't have a wired connection available.

I have made a backup of my /etc/network/interfaces, and removed all the entries in it (except lo).

Network-manager seems to work (it detects wireless networks around me), and when switching to wired network, it works too. However, it does not remember my settings when I reboot. Each time I boot my notebook, and login into Gnome, I have to select "Wired connection" manually, otherwise I have no internet connection. This is what I get when running nm-applet from a console when selecting wired network:

> ** Message: <information>       Forcing device '/org/freedesktop/NetworkManager/Devices/eth0'

** Message: <information>       You are now connected to the wired network.

I have searched the forums, and could not find a solution. Could somebody help me on this? Thanks!

P.S. I'm on Ubuntu Edgy.

---

### Post by Johan_SV on 2007-03-30
Anyone, please? It would suck if I would have to remove Network-Manager and use the old-fashioned way :(

---

### Post by mikewhatever on 2007-03-30
There seems to be no way to select a preferred network for gnome-nm. The tool is really a very basic one, so do not expect too much.

---

### Post by Johan_SV on 2007-03-30
> **mikewhatever said:**
> There seems to be no way to select a preferred network for gnome-nm. The tool is really a very basic one, so do not expect too much.

Hmm, I see, thanks for your reply. Is there perhaps something else you (or someone else) can recommend me (preferably not using KDE libs)? I really like the simple interface of gnome-nm.

---

### Post by mikewhatever on 2007-03-31
There are several other options in the repositories:
Network Selector 
Wifi-radar

and some more KDE based ones. I can hardly recommend any, since I haven't tried them. If you do, feel free to post an opinion.

---

