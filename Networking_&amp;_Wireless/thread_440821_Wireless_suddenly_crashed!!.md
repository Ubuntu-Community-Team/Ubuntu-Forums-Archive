---
title: "Wireless suddenly crashed?!!"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by jdriller on 2007-05-12
I was surfing my new wireless connection on my desktop and it just stopped working. When I run ifconfig I get info on my wlan0 but also a wlan0:ava. What's that about?

When I run iwconfig I get essid: off/any even though I've set this several times. It's not sticking. Access Point: not associated. I've set these through the command line AND through the gui in Network. Nothing's working.

When I try to restart the network I get a msg that says "No working leases in persistent database - sleeping"

My overall network is still healthy. I'm typing and accessing this site on my laptop right now through it.

I'm running 7.04 Fiesty, Belkin G usb network adapter. Ndiswrapper with the driver it came with. For some strange reason when i now try to open Windows Wireless Drivers, it asks for my password then dissappears. So I can't access it.


Any ideas what happened?

Jen

---

### Post by jdriller on 2007-05-12
Okay, got it working again. I went in and copied the rt73.cat file from cd to my /etc/ndiswrapper/rt73 folder. Then I followed the directions on this page : [http://ubuntuforums.org/showthread.php?t=261789](http://ubuntuforums.org/showthread.php?t=261789). Works well so far.

---

