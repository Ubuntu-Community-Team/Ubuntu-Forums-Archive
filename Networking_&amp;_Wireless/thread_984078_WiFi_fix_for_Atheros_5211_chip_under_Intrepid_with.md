---
title: "WiFi fix for Atheros 5211 chip under Intrepid with Ndiswrapper on Toshiba L305D Lapto"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by hwert on 2008-11-16
For weeks I have been chasing the problem wherein I could "see" the networks but was unable to DHCP to connect to any of them.  After much experimentation, the below "dirty fix" seems to work reliably. By placing it in /etc/rc.local it is executed each time a new runlevel occurs. 

Somehow Intrepid loses/breaks the DHCP connection when runlevels are changed. Perhaps this will shed some light to developers.  As to why this works is above my pay grade!


Add the following to the bottom of the file in /etc/rc.local

	modprobe ndiswrapper -r
	modprobe ndiswrapper -i

just before "exit 0"

Harry Wert
Physicist

Verifed 11/15/2008 Works with startup, restart, suspend, and hibernate

---

