---
title: "Can't connect to my home network"
date: 2016-08-22
forum: Networking &amp; Wireless
---

### Post by amadis2009 on 2016-08-22
Have not been able to connect to my home network since last night. This morning I can see my network but can't connect. I *can* connect to an unsecured wifi network, *and* I can connect to my home network through my Windows partition as well, just not on Ubuntu. Been having intermittent network connection issues lately. For a while the wifi would go out and I couldn't even see any other networks. The only thing that worked was restarting the computer. I checked the connection settings and noticed infrastructure mode is now called client mode and a new? option hotspot is there. I tried switching to ad-hoc mode and that helped a while. But now I can see all networks, but can't connect no matter what mode I'm in. It seems client and infrastructure are the same thing so I switched back to client but still can't connect. iwconfig says Access point not associated. I'm on 16.04 and my [FONT=verdana]adapter[/FONT] is a Rosewill RNX-N300X IEEE 802.11b/g/n. Has something changed in Ubuntu recently, or is my hardware or driver no longer compatible? Something else?

---

### Post by amadis2009 on 2016-08-22
Okay I just now disabled security on my router login page so I could see if it would connect without security. No go. But when I switched back to secured password mode and re-entered my password settings in Connection Information I am now connected. Don't know why it's now suddenly working when I had all the same settings before and it didn't work. Even rebooting hadn't worked, but now iwconfig shows an associated access point. If I don't have anymore problems by end of day, I'll mark this as solved.

ETA: Urrgh! Actually now my network connector says I'm connected to my home network but I don't actually have any internet access. All Internet browsers say no internet connection and internet dependent applications won't work. Please help!

---

### Post by amadis2009 on 2016-08-22
Checked my Ipv4 settings and apparently when I switched to the unsecured connection for a few minutes, Ipv4 switched to 'shared'. I switched back to automatic dhcp and all is well.

---

