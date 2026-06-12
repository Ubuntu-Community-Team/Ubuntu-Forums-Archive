---
title: "Creating wireless hotspot Lubuntu 16.04"
date: 2017-04-12
forum: Networking &amp; Wireless
---

### Post by old-marc on 2017-04-12
Hi peeps, I know this has been discussed before but the threads I've looked through haven't helped me unfortunately.

Basically I'm trying to set up a friends asus eeepc 904HD as a wireless repeater for them. I installed 16.04 as it is long term support but I wonder if I may have made a mistake here, as wireless hotspots appear to have been broken with this release. The setup I'm attempting to achieve is having the netbook pick up wifi signal then rebroadcast it. Now I've managed to get it to broadcast a hotspot but not pick up wifi at the same time, so phones etc. can connect to it but there's no internet. Ethernet cable is not an option.

I've done 'iw list' and the chip is capable of being used as an access point, but I can't get it to pick up wifi and broadcast it at the same time. Is there a solution to this, is it fixed in 16.10 or should I roll back to 14.04? Help much appreciated, thank you.

Asus EeePC 904HD
Lubuntu 16.04 LTS

PS. Current testing environment is my living room with the router just the other end of the room, so picking up wifi isn't an issue.

---

### Post by old-marc on 2017-04-14
Any ideas guys? Would be good if I could get this sorted. As much as I'd be happy to install different versions of lubuntu if needs be, I'd rather avoid it unless I know it's got a good chance of working.

---

### Post by old-marc on 2017-04-14
All sorted now, had a usb antenna which I realised was recognised as a separate device. So the antenna receives and the built in wireless transmits. Job done.

---

