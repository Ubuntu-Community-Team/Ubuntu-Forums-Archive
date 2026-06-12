---
title: "Open VPN not working in Ubuntu 14.04.2"
date: 2015-07-30
forum: Networking &amp; Wireless
---

### Post by drm200 on 2015-07-30
I'm using 14.04.2 on my laptop.     I installed the Open VPN plugin Gui for network-manager-gnome from the Ubuntu software center
	
I can log into the VPN server without problem.  However there is no internet connection.

I can ping googles servers 8.8.8.8 and get a proper reply.
However, if I ping google.com .... there is no reply.

So it appears that the DNS is not working.

After many hours of searching, I found this suggestion:

	sudo gedit /etc/NetworkManager/NetworkManager.conf
		Change
			dns=dnsmasq
		to this:
			#dns=dnsmasq


	Then, restart NetworkManager:  sudo service network-manager restart

This appears to fix the broken Open VPN connection, and I can now browse without problem.

However, I concerned about the solution .... Would this solution in anyway compromise the VPN??  Are there side effects that I should be aware of??

---

