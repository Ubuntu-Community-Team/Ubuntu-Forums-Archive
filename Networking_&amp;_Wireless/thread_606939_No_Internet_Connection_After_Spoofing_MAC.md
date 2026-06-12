---
title: "No Internet Connection After Spoofing MAC"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by lespaul_rentals on 2007-11-08
I have been using Linux on my laptop for a while now, and it all worked fine until I just recently re-installed Ubuntu 7.04.  I like to go wardriving and Wi-Fi hunting in my spare time, and I will always spoof my MAC address before setting out.  I discovered, however, that while Ubuntu recognizes and handles my wireless card perfectly, if I spoof my MAC and bring the interface back up, I can no longer connect to a network.  Network Manager or a scanner like wifi-radar will not be able to pick up additional networks as I drive around.  It's like the wireless card permanently dies when I spoof the MAC address, whether it's through the **ifconfig** command or an application like macchanger.

I've even tried Kubuntu, MEPIS, Linux Mint...you name it.  The same problem occurs on all distros.  I cannot figure out why, because I've been using my laptop for wardriving for a couple of months now, and I could always spoof my MAC address with no problem.  Also note that I can connect to hotspots just fine so long as I don't mess around with my card, it's only after I spoof my MAC that a problem appears.

Why would this problem suddenly spring up?  Better yet, what can I do to fix it?

---

### Post by lespaul_rentals on 2007-11-11
Sorry for the bump, but if anyone could help me I'd really appreciate it!

---

### Post by pieisgood4589 on 2007-11-11
OK, the same thing happened to me in Ubuntu. Apparently, the restricted drivers in Ubuntu (the ones you have to use to setup wireless cards) doesn't like it when you spoof your MAC address. I don't know why. I just stopped doing it. :lolflag:

---

