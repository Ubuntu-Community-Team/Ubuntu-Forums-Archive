---
title: "eth0 gone...?"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by vamp4life666 on 2008-01-24
[solved] I had to switch my HD out of one dell box into another. 
7.10 boots with no problems but my eth0 is giving me trouble.

ifconfig dose not show eth0 at all and /etc/network/interfaces shows

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


and thats all


sudo /etc/init.d/netwroking restart (and force-reload) yeilds: ERROR while getting interface flags: No such device
there is already a pid file /var/run/dhclient.eth0.pid with pid 134619120

sudo lshw -C netwrok    gives me
*-network DISABLED
description: Ethernet interface
product: 82540EM Gigabit Ethernet Controller
vendoer: Intel Corperation
physical id: c
and more specs.....

lshw -v    gave me
Ethernet.... Intel.... Gigabit...
Subsystem: Dell Gx260
Flags: bus master, 66MHz, medium devsel, latency 64. IRQ 18
Memory at ff8e0000 (32-bit, non-prefetchable) [size=128K]
I/O ports at eccc0 {sike=64K]
Capabilities: ,access denided>

i would image i need to reset the netcard or renew the dhcp lease.. i'm just son't know how...
suggestions please...

---

### Post by gfowler on 2008-01-24
> **vamp4life666 said:**
> I had to switch my HD out of one dell box into another. 
7.10 boots with no problems but my eth0 is giving me trouble.

ifconfig dose not show eth0 at all and /etc/network/interfaces shows

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


and thats all


sudo /etc/init.d/netwroking restart (and force-reload) yeilds: ERROR while getting interface flags: No such device
there is already a pid file /var/run/dhclient.eth0.pid with pid 134619120

sudo lshw -C netwrok    gives me
*-network DISABLED
description: Ethernet interface
product: 82540EM Gigabit Ethernet Controller
vendoer: Intel Corperation
physical id: c
and more specs.....

lshw -v    gave me
Ethernet.... Intel.... Gigabit...
Subsystem: Dell Gx260
Flags: bus master, 66MHz, medium devsel, latency 64. IRQ 18
Memory at ff8e0000 (32-bit, non-prefetchable) [size=128K]
I/O ports at eccc0 {sike=64K]
Capabilities: ,access denided>

i would image i need to reset the netcard or renew the dhcp lease.. i'm just son't know how...
suggestions please...

I would suspect that you did not swap the network card, and the MAC address has now changed.  Until Gutsy one would go to /etc/iftab and comment out the mac address and reboot. Now go to /etc/udev/rules.d/70-persistent-net.rules and comment out the line that has NAME="eth0" in it and reboot.  All should be well and you will find eth0 back in business.

Jerry

---

### Post by vamp4life666 on 2008-01-24
I cam across the comand ifconfig -a   which gave me eth1 with all the specs that should pop up.

So i tried added eth1 to /etc/network/interfaces    and it poped up in the ifcofig withou even rebooting.     

and i'm back in buisness...

thatnks for the response i'll give it a try and see if i can get back on eth0

---

