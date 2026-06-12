---
title: "Windows vs Ubuntu wireless strength"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by thrillhouse on 2006-09-09
I am currently in between internet providers (just moved).  I now live in a mostly college apartment complex where about half of the wireless networks are unprotected.  I’ve noticed that if I boot to Ubuntu, I have pretty sketchy wireless connectivity, but while in Windows, I have almost flawless connectivity with the same SSID.  I’m using net manager applet to run my wireless connection in Ubuntu.  I guess I’m just curious but any ideas would be great.

---

### Post by thrillhouse on 2006-10-12
Ok, I now have my own internet.  I am sitting less than 8 feet from my wireless router, and my networkmanager connection strength varies from 48-85%.  The wireless strength is turned up to 100% on my router.  Whats the deal??

---

### Post by twistedtwig on 2006-10-12
I have heard that wireless strength doesnt mean much.  As long as you have a connection u have a connection.

A friend said he did a test on the transfer speeds of cards saying weak and strong and found no difference.

I would be curious to hear what others think / know on the subject.

Twiggy

---

### Post by KingArthur10 on 2006-10-12
Agreed with the above post.  Wireless signal strength varies by the way it is calculated.  Linux is just picky with its calculation, I guess.  As long as you are over about 40%, you're probably good.  Also, if there are several other wifi networks in the area, the signal to noise ratio decreases causing increased interference and thus, a poorer connection percentage.

---

### Post by tlsarles on 2006-10-12
Have you looked at the Channels? If you are in a place with lots of access points around, they could be interfering with each other, which can cause the signal strength to appear to fluctuate. To see what channel APs are running on around you, use Net stumbler for windows or kismet for Linux. Most routers default to ch6, so you may want to change yours if you have not. Also note that only 3 channels don't overlap; 1, 6, and 11. So if everyone around you uses 6, and you set yours to 7 because its free, you are still getting a lot of noise from other networks.

---

