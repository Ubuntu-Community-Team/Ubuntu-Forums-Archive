---
title: "wireless now working, but not shown in GUI"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by metafizx on 2007-07-16
Hi,

I finally bumbled through getting the Broadcom 4306 working on my HP Pavillion Laptop
(Ubuntu Fiesty) 

But I have a little issue now with the Gnome Desktop, where you can choose the network (either wired or wireless) by the network icon in the right side of the upper toolbar. For some reason only the wired connection, and manual configuration is shown. There is no wireless selection.

but the wireless is working fine ! I have the correct wireless station up and running with it's WEP and DHCP.

When I open up the Network settings, I can see the wireless and wired are present. It's just the wireless doesnt show up in the network part of the toolbar on the desktop.

I'd like to fix that, and also know how to determine what network I am connected to, and how to tell what the DHCP has set the IP address to. Is there a simple tool to show me this info ?

thanks for any help on this...

---

### Post by steevols on 2007-07-16
You could try Wifi-radar, an oldie but a goodie. I'm fairly sure its in the repositories.

---

### Post by metafizx on 2007-07-16
thanks, I'll check on that..

someone suggested to install "network-manager-gnome"

here are a few quick things I learned...(sorry n00b)

**iwconfig** manipulate the basic wireless parameters
**iwlist** allow to initiate scanning and list frequencies, bit-rates, encryption keys... 
**iwspy** allow to get per node link quality iwpriv allow to manipulate the Wireless Extensions specific to a driver (private) 
**ifrename **allow to name interfaces based on various static criteria 
 
**ifconfig -a** gives you information on the interfaces 
what you want should be in /etc/resolv.conf 


the n00b learns...

but, I have no idea how to fix the network icon in the Gnome Desktop. Prior to mucking around with the Broadcom 4306, there used to be something in the dropdown about wireless. But now it just says "wired" and "manual configuration".
:confused:

---

