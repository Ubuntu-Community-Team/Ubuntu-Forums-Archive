---
title: "No VPN &amp; network applet update delay"
date: 2014-11-17
forum: Networking &amp; Wireless
---

### Post by ayami2 on 2014-11-17
I am no longer able to open a VPN connection through the GNOME network manager applet. This appears to have started after updating to Ubuntu 14.10 (hadn't used VPN for a couple weeks before update, so I can't be sure it wasn't already broken). VPNs are still listed in the network manager applet but nothing happens when I click on one to connect. Normally is use an Openconnect VPN, which starts with a connect/authenticate window, but now nothing opens at all when I select it from the VPN menu. I have tried re-creating the connection, as well as a test PPTP VPN. Nothing happens when selecting any of the VPNs from the applet menu.

However, I know Openconnect is still working because I can manually connect using the commandline. I have reinstalled openconnect, network-manager-openeconnect and network-manager-openeconnect-gnome to no effect.

Also, there is an update delay in my network applet. After creating a new VPN it does not show on the menu until after I disable and then re-enable networking entirely.

I assume it is a problem with the network manager applet but I am not sure how to further debug.

---

