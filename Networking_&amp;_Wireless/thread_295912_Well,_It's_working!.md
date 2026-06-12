---
title: "Well, It's working!"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by orian on 2006-11-08
I just want to share my success in getting wireless up and running. My problem was with encryption (see earlier post). Each attempt to connect to my router disabled my wireless. I confirmed this through iwconfig. The solution was to install NetworkManager-gnome and editing my etc/network/interfaces file so it only read:

auto lo
iface lo inet loopback

Once this was done my wireless enabled, this allowed me to enter my encryption info and Bob's your uncle. It's still working after several reboots and changing to other wireless networks such as on the Train or Internet cafes. 

I'm using a Thinkpad T43 with an Intel Pro-wireless 2200. OS = Edgy.  I found the instructions mostly in this forum and some through just googling.

I'm very thankful for this forum

orian--untethered

---

### Post by ThrobbingBrain66 on 2006-11-08
we have a very awesome community here and i am glad you sorted everything out

happy ubuntuing,
brad

---

