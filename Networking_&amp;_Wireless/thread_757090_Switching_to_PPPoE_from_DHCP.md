---
title: "Switching to PPPoE from DHCP"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2008-04-16
I'm running nm-applet 0.6.5 with a wireless card and router.  I recently had to change ISP's and they had me change the way my router was working from Automatic Configuration - DHCP to PPPoE.

I realized that I wasn't connecting to the router with my server anymore, (I'm running Xfce to make life easier) so I changed nm to allow for roaming - everything works great.  But I would like to have that machine with a static IP address so I can do some port forwarding through the router.

So I click on the icon, select Manual configuration, and select Wireless, go into the properties and turn off roaming, select the ESSID from the drop-down, select WPA Personal as the security, enter the password, select Static IP address under the Configuration options, give it an address of 192.168.1.200, give the netmask as 255.255.255.0 and the gateway address as 192.168.1.1 - and nothing. Even rebooted with the new settings.

I can, however, browse the machine with other computers on my network.

The Roaming/Manual mode is an Ubuntu-specific patch to NetworkManager, so the Ubuntu network config tools are setting up the card.

Any ideas on where to look?

---

