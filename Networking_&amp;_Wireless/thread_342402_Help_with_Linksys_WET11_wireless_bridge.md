---
title: "Help with Linksys WET11 wireless bridge"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by Noah0504 on 2007-01-20
I'm trying to get my Linksys WET11 wireless bridge to work with Ubuntu.  I've tested it with another computer in my home running Windows XP, and it worked fine.  I'm not even sure what would be causing the problem, so it's hard to really tinker with anything.  I know the bridge works, I just can't get Ubuntu to form a connection with it.

---

### Post by teaker1s on 2007-01-20
try a numeric ip address if that will open a page then ubuntu is failing to resolve the DNS server ip

---

### Post by Noah0504 on 2007-01-21
Well, I think I have it working for the most part.  I had to give it a static IP address which doesn't make sense.  The bridge has it's own IP address of 192.168.103 that I gave it when I configured it, but under Ubunut, it has an IP address of 192.168.1.100 that I configured under networking.

---

### Post by teaker1s on 2007-01-21
ubuntu must see the bridge and the bridge must be set so it's acting as a hub

---

### Post by Noah0504 on 2007-01-21
> **teaker1s said:**
> ubuntu must see the bridge and the bridge must be set so it's acting as a hub
I don't completely follow.

---

### Post by teaker1s on 2007-01-21
okay well a wireless bridge can be set so in effect it obtains an ip and essentially acts seamlessly like an Ethernet cable. 
Or if you connected a network switch so you have more than one Ethernet port and the wireless bridge/access point and configured it correctly it would allocate ip addresses to the computers connected to it

---

### Post by Noah0504 on 2007-01-21
Okay, I think I get it.  So really, the way I have it configured right now is correct?

---

### Post by teaker1s on 2007-01-21
yes if it's working then don't worry

---

