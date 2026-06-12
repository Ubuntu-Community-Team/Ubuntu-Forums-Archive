---
title: "D-Link DWL-G122 Slow Connection"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by webmaster_ph on 2008-07-19
Hi Folks,

I'm using a D-Link DWL-G122 (version C1) WIFI USB Adapter which is installed on a Intel P4 Desktop with 1GB RAM and 256 MB Video.

Since upgrading to Hardy I noticed that I'm getting very slow speeds like less than 10 kbps on a LAN. There are about 11 workstations that are wirelessly connected to a D-Link router.

The adapter is listed as [supported hardware]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") so compatibility may not be an issue. Its been two long months and there seems to be no solution.

Pls. help.

---

### Post by webmaster_ph on 2008-08-13
bump...need help pls.

---

### Post by codehawk on 2008-09-25
I'm experiencing the same problem. The USB stick is functional (signal strenght is actually very good), but the connection speed is very slow. 
nm-applet actually tells me it's connected at 1mb/s.
It also indicates that the driver used is rt73usb.

---

### Post by bryanl on 2008-10-03
on another thread about the rt2500 the suggestion was to

> Type iwconfig. If you see in your wireless interface Bit Rate 1 Mb/s type sudo iwconfig xxxxxx rate 54M

xxxxxx should be the name of your wireless interface

or

> For have 54M from beginning you can add pre-up iwconfig wlan0 rate 54M  in /etc/network/interfaces and then restart your wireless by sudo /etc/init.d/networking restart. Then your wireless should work from beginning with full speed.

Do you use WPA or WEP? I only can use this solution with WEP. With WPA it doesn't work.

There is also a bug report [https://bugs.launchpad.net/ubuntu/+s...22/+bug/134660](https://bugs.launchpad.net/ubuntu/+s...22/+bug/134660)

seemed to work for many. easy enough to try.

---

