---
title: "Belkin F5D6001 card : 'Radio of your wireless card seems to be turned off.&quot;"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Littleweseth on 2006-12-17
G'day;

I'm trying to get a Belkin Wireless Desktop F5D6001 card working using wlassistant. When i start up wlassistant (from a root terminal), it asks me 'Radio of your wireless card is off. Would you like to turn it on?', after which it scans for a while and comes back with 'Radio of your wireless card seems to be turned off using an external switch on your computer.'

More interesting than these dialogs is what is being outputted to the terminal. From startup to when I close the wlassistant window, this is what I see;

> root@pellinore:/home/lws# wlassistant &
[1] 5342
root@pellinore:/home/lws# X Error: BadDevice, invalid or uninitialized 
input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

Wireless interface(s): eth1
Permissions checked.
radio_on: /sbin/iwconfig eth1 txpower auto
ifconfig_status: /sbin/ifconfig eth1
scan: /sbin/iwlist eth1 scan
==>stderr: eth1      Failed to read scan data : Resource temporarily 
unavailable

No networks found!
Radio switch seems to be off.

==>stderr: eth1      Failed to read scan data : Resource temporarily unavailable seems to be the niggling part, but I may be wrong.

I physically removed the card and checked for a toggle switch, but as expected there were no switches to be found. lspci lists the card as being there and modprobe shows that the driver (adm8211 multicast) is loaded, so drivers are probably not the issue. Interestingly, the power LED seems to be pattern-blinking - i don't think it's analogous to PC speaker pattern beeping indicating a specific fault during POST, but i may be wrong.

I've also disabled ipv6 as per the Wireless Troubleshooting guide at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) to no avail.

The computer (pellinore) is a slightly strange install - it started off as a server install and later got xubuntu and openbox installed on it, and i've installed several different wireless-related packages - for all i know, maybe there are wireless autoconfiguration daemons squabbling with each other.

Any help welcomed, but the most welcome help is that which gets my wireless working :p I'm itching to see if this here parabolic reflector glommed onto my antenna actually does anything - considering it's constructed from styrofoam, cardboard/alfoil and copious stickytape, maybe not :)

-lws

---

### Post by Littleweseth on 2006-12-17
Bump.

---

### Post by Littleweseth on 2006-12-18
Bump x2.

The friend whose wireless card this is reports it to work (albeit with some bludgeoning) under windows, so it's not a harware fault.

---

### Post by Littleweseth on 2006-12-21
final bump.

---

