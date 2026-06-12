---
title: "RT2571 chipset &quot;works out of the box&quot; is a lie."
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by CatSpin on 2008-08-09
I have a wireless issue that is driving me a bit mental!

So after untold problems and hours of help files with my windows compatible wifi card I decide that I couldn't spend any more time on it. So I head over to the [Linux Emporium]("http://www.linuxemporium.co.uk/") to get a Linux compatible wifi device.

[Edimax 54 Mbps Wireless USB stick with Antenna]("http://www.linuxemporium.co.uk/products/wireless/#pidR26728") (the device uses a RT2571 chipset)
(from [this]("http://www.linuxemporium.co.uk/products/wireless/") page)

Not wanting to take any chances with the various commands (few of which I actually understood!) I wiped my system with a fresh download of Hardy 8.04.

From what I understand, this device should work out of the box. Yet when I right click on the network icon in the top right, I get no "Wireless Networking" option.

I tried some commands included on the suppliers troubleshooting manual but to no avail (see below)

> 
root@Home:~# dhclient rausb0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
rausb0: ERROR while getting interface flags: No such device
rausb0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
root@Home:~# ifdown rausb0
ifdown: interface rausb0 not configured
root@Home:~# ifup rausb0
Ignoring unknown interface rausb0=rausb0.
root@Home:~# iwlist rausb0 scan
rausb0    Interface doesn't support scanning.


Can anyone offer any advice or perhaps more information would be required?

---

### Post by jimv on 2008-08-10
The site says that the card came with a driver disk...albeit for older versions of Ubuntu.  Perhaps you could give those drivers a try anyway, since it's not working.

---

### Post by CatSpin on 2008-08-10
> **jimv said:**
> The site says that the card came with a driver disk...albeit for older versions of Ubuntu.  Perhaps you could give those drivers a try anyway, since it's not working.

Yeah, the manufacturer's disk comes with some drivers but not for Ubuntu. Drivers included are for Debian, Febora and SuSE. Am I right in thinking that the Debian driver would be most appropriate?

---

### Post by Tom--d on 2008-08-10
> **CatSpin said:**
> Yeah, the manufacturer's disk comes with some drivers but not for Ubuntu. Drivers included are for Debian, Febora and SuSE. Am I right in thinking that the Debian driver would be most appropriate?

ubuntu is Based on Debian. Go with that :)

---

