---
title: "Some Wireless frustation..."
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by KurtB on 2006-08-06
Hello,

(fyi: I've got a Belkin54g broadcom-based WIFINIC)

I've testing Ubuntu & wireless since Hoary: didn't work
Upgraded to Breezy: work nicely using ndiswrapper...
Upgraded to Dapper: dead...

No problem, there's a forum with probably enough threads concerning this bloody-chipset...

So I tried almost any thread dealing with this WIFINIC.

Under Breezy, WiFi just worked with the bcmwl5a.inf file that came with the driver-CD, once upgraded to Dapper: blacklisting the bcm43xx enables the power led on the NIC but disables the wlan0 interface in the "network" section. Whitelisting enables the wlan0 interface in the network section, but the NIC stays dead on booting.

the driver and hardware are (re-)installed and recoginzed when I "sudo ndiswrapper -l"...

Since upgrading to Dapper I've been trying almost any method to get my Wifi back up and runnning,...without any luck

So:
Is there anyone with an idea left for my wlan0 before I leave Ubuntu aside permanently? 

I was very pleased with Breezy, and hoped that common problems concerning this broadcom chipset would have been fixed with the newer releases...damn...this is frustrating...

Fyi:
- bcmwl5a.inf worked under breezy, so I hope it still does under dapper
- driver installed and ok, modprobe ok
- blacklisted: ok
- iwlist wlan0 scan = dead

---

