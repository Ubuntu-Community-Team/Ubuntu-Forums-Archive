---
title: "MA521 trouble"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by l951b951 on 2006-12-30
Hi, I'm new to linux jumping in feet first.  I am having trouble with my wlan0.  It seems to be recognized; I can see my network; I just can't get it to connect.  I am at my wits end, I spent 5 hours working on this problem.  I have searched the forums and tried every solution given with this card.  Can someone help me?  I am comfortable with a command line, but I haven't memorized all the commands, so I need details.  I'll buy you a beer if you can help.

**_Hardware:_** 
   Compaq Evo N610c - Ubuntu Dapper Drake (Downloaded, burned, installed, and updated on 12-28-06)
   Netgear MA521 wireless card (power and link light are on)
   Linksys WRT54G wireless router set up with a 10 digit wep key

**_ndiswrapper -l returns this:  _**
 Installed ndis drivers:
netma521                driver present, hardware present

I've tried using ndiswrapper and iwconfig to get connected; it will scan and see my router, but won't connect.

wlassistant
Using the terminal I run "sudo wlassistant" (after installing with synaptic).  Running it (a gui) causes this to be displayed in the terminal
> X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): wlan0
Permissions checked.
ifconfig_status: /sbin/ifconfig wlan0
scan: /sbin/iwlist wlan0 scan
Networks found: 1
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.

Using the gui if I try to connect I get this:

> kill_dhcp: /sbin/dhclient -r wlan0
==>stderr: Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:09:5b:63:40:6a
Sending on   LPF/wlan0/00:09:5b:63:40:6a
Sending on   Socket/fallback
ifup: /sbin/ifconfig wlan0 up
iwconfig_set: /sbin/iwconfig wlan0 mode managed channel 6 key restricted s:725cffa4fb essid PIMPTASTIC
==>stderr: Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Operation not supported.
iwconfig_ap: /sbin/iwconfig wlan0 ap 00:16:B6:B9:F7:20
ifconfig_dhcp: /sbin/dhclient -q wlan0
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed


I can see the network, But I can't connect.  What am I missing?

---

### Post by l951b951 on 2006-12-30
I installed network manager (nm-app I think), rebooted, and it magically lets me enter my wep key into a gui and connect to both my home and business wlan.

I'm still not sure what happened, but I'm glad it finally decided to "just work".


After several weeks of intermittent connectivity, I narrowed it down to the fact that either my card or the RTL8180 driver was defective.  I went out and bought a Netgear WG511T (after reading several forum posts that it worked out of the box).  I have no alliegance to netgear, but the forums seemed to say this card had the Atheros chipset and would work.  It did.  No problems, no twiddling.  3 weeks later with near daily use, the card is still working flawlessly.

---

