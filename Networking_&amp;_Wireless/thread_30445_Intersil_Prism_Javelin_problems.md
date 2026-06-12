---
title: "Intersil Prism Javelin problems"
date: 2005-04-28
forum: Networking &amp; Wireless
---

### Post by Heliode on 2005-04-28
Good evening everyone. It looks like I might need some help here...

I have the following problem with my mini-PCI wlan network card; It has always been detected by Ubuntu but I never tried using it until I bought a wireless access point today, and the thing doesn't seem to work. When I have a look at the network management GUI, it is listed there as eth0. However, when I try to connect it to the wlan, it won't work; just tries to activate it for a while and then stops with the interface deactivated. 'iwlist eth0 scan' also doesn't give me any results. 

This is the card as it shows up in lspci:

```

0000:02:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

```

I found these lines in dmesg. Thought they might be of some use.

```
Loaded prism54 driver, version 1.2
prism54: request_firmware() failed for 'isl3886'
prism54: request_firmware() failed for 'isl3886'
prism54: request_firmware() failed for 'isl3886'
prism54: request_firmware() failed for 'isl3886'
prism54: request_firmware() failed for 'isl3886'
prism54: request_firmware() failed for 'isl3886'
prism54: request_firmware() failed for 'isl3886'
prism54: request_firmware() failed for 'isl3886'
prism54: request_firmware() failed for 'isl3886'

```

I have a laptop, also running Ubuntu, sitting right next to the PC, and its wireless interface has a link strength and signal quality of 100%. 
Also, on the PC in Windoze it works fine with 'excellent' link quality. 

I hope somebody can help me with this. I've tried setting up the access point in lots of different ways but nothing works, so it must be the card itself. I'm not a complete n00b with Linux + wireless, since I've had to go through quite some crap to get the wireless interface on my laptop to work. I have absolutely no idea where to go from here, so any suggestions are very welcome!

Thank you very much in advance!

---

### Post by predator29 on 2006-04-11
I've posted a solution at this thread:
[http://ubuntuforums.org/showthread.php?t=35949](http://ubuntuforums.org/showthread.php?t=35949)

---

