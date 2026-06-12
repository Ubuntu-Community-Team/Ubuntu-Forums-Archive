---
title: "no connection"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by gordonsmall@bellsouth.net on 2008-11-11
I have a Compaq Presario V2665US laptop running Windows XP.  This laptop has an AMD 64 Mobile Processor (1.8 Ghz) with 1 gig of RAM.  

I have a home wireless network using a Belkin Wireless G router – 802.11g.  According to the Windows System info the laptop has a Broadcom 802.11b/g WLAN driver and a 1394 Net Adapter. The router is configured to allow WPA/WPA2 clients, and is password protected.

When running WindowsXP on the laptop, it automatically finds and connects to my network and runs well.  I also have a Zonbu mini computer running a version of Linux, and it also readily connects to my network with simple,intuitive instructions.

When I read that Ubuntu 8.10 provided better support for wireless networks, I quickly loaded it on my laptop.  However, when I hold the mouse icon over the network icon in Ubuntu, I get the message “No network connection”.

If I left click on the symbol (double clicking does not change anything), the Wired Network, Wireless Networks are grayed out – only the VPN connections, Connect to hidden Wireless Connections, Create New Wireless network are active. I have tried different settings under the hidden Wireless Connections, all to no avail. Based on something I saw on the web, I went to System-Admin-hardware drivers.  All that came up was a note about a proprietary graphics driver – no other drivers were shown.

I went to the Synaptic manager to see what was loaded in the way of wireless support, and the installed packages are wireless-tools, libiw29, pcmciutils, jockey-gtk, wpa supplicant, jockey-common, libopenobex1. This is Greek to me, but may be helpful to someone:)

After downloading some troubleshooting instructions, I tried the Terminal command: sudo 1shw -C network.  It shows the wireless interface, but says it is disabled.  My laptop has an on/off switch for the network, but that switch is on.

Does anyone know how to enable this wireless interface on Ubuntu 8.10?

Gordon Small

---

### Post by crystal eyes on 2009-02-20
update to network manager 7 first



right click network manager on the try then select enable wireless network
that should work.



mar

---

### Post by gordonsmall@bellsouth.net on 2009-06-02
Thanks for the response.  Will give that a try.

Gordon Small

---

