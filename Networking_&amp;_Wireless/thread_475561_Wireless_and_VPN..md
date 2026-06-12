---
title: "Wireless and VPN."
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by WesHinsley on 2007-06-16
Hi all,

I'm struggling with a wireless and VPN situation - I'm needing to firstly connect to the wireless network at my workplace, (which is not secure - no WEP or WPA), and then open a VPN connection, which gets me access to the computers I need (namely, an svn server).

In roaming mode, Network manager never connects to the wireless - it doesn't seem to ask for an ip address. If I open a terminal and type "sudo dhclient ra0", it requests an IP address, gets it, and I can browse the web in Firefox. However, Network Manager still says "Not connected", and my VPN network is greyed out. 

If I take the wireless out of "roaming" mode, type the wireless network name, and specify "dhcp" in the list, then Network Manager successfully picks up the wireless connection. However, then "VPN" menu isn't available from Network Manager - the only item on the menu is "Manual Configuration", so I can't start the VPN...! So either way, I can't get both wireless and VPN up.

Any ideas?
Thanks,
Wes

---

### Post by FrancoNero on 2007-06-19
I got the vpnc thing and it gives me the option in the network manager correctly. however, when i select the vpn profile and enter my login data, it crashes the nm-applet..
also, i have a authentication certificate file that i somehow have to import into the vpn client. how do I do that?

---

### Post by azcoffeehabit on 2007-07-07
I am also seeing the issue where the wireless-manager vpn settings does not appear when I disable the Wired connection in the nm.  When the wired network is enabled and I select the vpn I wish to connect to I am receiving this message in the syslog.  The wireless connection is enabled and connected to the internet.  The wired connection is not.  

NetworkManager: <WARNING>^I nm_vpn_manager_activate_vpn_connection (): nm_vpn_manager_activate_vpn_connection(): no currently active network device, won't activate VPN. 

It looks to me that the nm vpn plugin cannot work on anything but eth0??  The wireless card on my computer is eth1.

Any ideas?

-Paul

---

