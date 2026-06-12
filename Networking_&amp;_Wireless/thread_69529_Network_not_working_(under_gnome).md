---
title: "Network not working (under gnome?)"
date: 2005-09-27
forum: Networking &amp; Wireless
---

### Post by ominolore on 2005-09-27
Hi everybody,
I've been using Ubuntu Linux just for some months, but I keep on having a big problem with my network, I'm not able to solve.
I've got a small LAN with a DSL router (ip: 192.168.1.1) working both as ethernet and wi-fi device, and my network seems to be configured well: LAN Internal addresses are working fine, i've set folder sharing with samba, and everything works veeery good.
BUT when I try to connect to the Internet (using Firefox, Epiphany, Synaptic, Gaim, or everything else) I always have a timeout error, EVEN IF I can successfully ping any host on the web (just for being clear: if I ping google.com is always okay). The strange thing is that the Konqueror browser works with no problem, while all the other programs do time out all the times.

Can anybody help me out? I'm kind going crazy with this affair.. thank you so much.
Lorenzo

PS. I'm posting you my /etc/network/interface, as it is right now:


# This file describes the network interfaces available
on your system
# and how to activate them. For more information, see
interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug
subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet static
wireless-essid OPENLAN
address 192.168.1.2

netmask 255.255.255.0
gateway 192.168.1.1
auto wlan0

auto eth0


...WHERE IS THE PROBLEM??? Please help me.. I don't want to reboot in Windows.. I don't like it.. can anybody understand me? Okay.. just joking, thank you anyway.

---

