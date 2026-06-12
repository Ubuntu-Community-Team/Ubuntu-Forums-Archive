---
title: "Unstable WiFi"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by mr.loco on 2008-03-31
Hey guys

I'm having some issues with my Linksys PCI card (not sure of what model it is, but it "works" straight ou of the box)

The problem is that it works fine for about 5 minutes and then it just stops. iwconfig says i'm  connected but iwlist just tells me that there are no scan results.

any pointers?

maybe I should try ndiswrapper?

thx.

[edit]

I've found out what the net card is: WMP54G (4.0)

sorry for not posting more info, but i can't really do anything since the computer in question is offline

---

### Post by chili555 on 2008-03-31
I think your answer is here: [http://ubuntuforums.org/showthread.php?t=728909&highlight=WMP54G](http://ubuntuforums.org/showthread.php?t=728909&highlight=WMP54G)

---

### Post by mr.loco on 2008-03-31
Actually, the solution to this problem seems to be [here]("http://ubuntuforums.org/showthread.php?t=627030")

I looked up the driver name in the device manager thingy and searched it on the forums (really that should have been the first thing to do)

I'll let you know if that sorts things out.

[UPDATE]

rt61 is giving me errors when compiling

/facepalm

---

### Post by chili555 on 2008-03-31
> rt61 is giving me errors when compilingWhat errors? May we help you?

---

### Post by mr.loco on 2008-03-31
Thanks alot mate but i just ended up using ndiswrapper, works like a charm :)

:guitar:

unless you want to see the error logs, if so I can post them.

---

