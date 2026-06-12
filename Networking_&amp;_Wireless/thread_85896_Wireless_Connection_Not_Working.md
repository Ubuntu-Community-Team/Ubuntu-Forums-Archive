---
title: "Wireless Connection Not Working"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by Pyrocuror on 2005-11-03
I have a fresh install of Breezy, and everything seems to be working fine except for the wireless.  I am using a Dell TrueMobile1100 series card (rebadged Cisco card that uses Aironet drivers).  The card was detected during the installation, so I chose to use it as the default (eth1) connection.  When I go into the network configurer everything looks fine- DHCP is selected, it see's my AccessPoint and ESSID, etc.

I've been poking around on these forums for a couple hours now, and tried various things that have been posted to no avail.  The only thing I have  modified is my /etc/network/interfaces (after reading another thread) and mine now looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth1

# The primary network interface
iface eth1 inet dhcp
wireless-essid any
auto eth1


When I try to ping my router it says Network is unreachable.

When I run iwconfig the card see's my ESSID, the MAC address, etc.

When using sudo ifup eth1 I get an error saying NO DHCPOffers received.

dmesg does not reveal any errors about airo.

Any ideas?

---

### Post by Pyrocuror on 2005-11-03
Well, while playing around some more I noticed an eth2 connection.  I activated that one, disabled eth1, and voila!  *shrug*

---

### Post by wylde342 on 2005-11-07
Just to help anyone out where I was, I had this exact same issue that the author stated; an additional interface.

sudo ifdown eth1
sudo ifconfig eth2 up
sudo iwconfig eth2 essid "essid" (w/o quotes, your essid)
sudo iwconfig eth2 key "1111-1111-11
sudo dhclient eth2

Voila!

---

