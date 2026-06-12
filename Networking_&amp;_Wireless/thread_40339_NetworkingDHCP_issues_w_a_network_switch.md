---
title: "Networking/DHCP issues w/ a network switch"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by _cashel on 2005-06-08
First off, my ubuntu machine works flawlessly when connected to my router w/ other computers. However it's when it's on a network switch that it gives me trouble. 

The first problem occurs when I unplug the Ubuntu box from the router and in to the switch. My Windows box will identify that it's no longer connected, but will assign a new IP (not the typical 192.168.x.x, it's 169.254.x.x) after giving me an error saying 'limited connectivity.' The Ubuntu box will just sit there and do nothing. As expected it can't browse the network or do anything like that. What can I do to make it automatically recognize what is going on and then assign a new IP so it will be on the Windows network? 

The second issue involves Samba. I've installed it, but whenever I reboot and Ubuntu loads, it says that the Samba daemons failed to load. How can I fix this? Could this be related to my first problem?

Thanks for the help.

---

### Post by defkewl on 2005-06-08
Could you please give a schema how your router, switch, win box and ubuntu box related?

---

### Post by _cashel on 2005-06-09
Yeah, sorry if it's somewhat confusing. Basically I have a simple network consisting of 2 Windows boxes and the Ubuntu box on a router sharing a dsl connection. I regularly host lan parties and use a switch to connect all of the computers on a standard network. The router and switch are NOT together, they are two completely separate networks. I just have them side by side right now to try and fix this problem I'm having. All the computers have DHCP enabled and auto receive IP's.

---

### Post by PhilippWollermann on 2005-06-09
Windows uses APIPA (Automatic Private IP Adressing) in case there was no DHCP server, but the user insisted on automatic configuration of the network card. When you connect only to a switch (and not to a router), there is no DHCP server. Ubuntu will appear to hang on boot, because it searches, and searches, ... but then continue (just wait a little longer) to boot without bringing the interface up.

You have to configure static IP adresses, as Ubuntu doesn't do a Zeroconf configuration (as APIPA is called by anyone but Microsoft ;)), or you have to install a zeroconf program, which gets a 169.254.x.x address for your Ubuntu Box too.

If you want to configure static IPs, just wait until it's finished with booting:

ifconfig eth0 192.168.2.10 netmask 255.255.255.0 up

Do it as root, or prepend "sudo". Then configure the other machines to also use adresses in the range of 192.168.2.x. This change isn't permanent - after a reboot, Ubuntu will retry to use DHCP to get an adress.

Philipp

---

