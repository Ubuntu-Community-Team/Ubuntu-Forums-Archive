---
title: "ndiswrapper kernel panic"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by anton.b on 2005-11-15
Since I've upgraded to Breezy, ndiswrapper seems to behave rather strange in combination with a USR805410 WLAN PC CARD (I've checked the behaviour on two laptops). Every now and then, during boot-up, the network won't initialize and the computer freezes. At first, I thought it wasn't a big deal and just restarted the PC, after which it usually worked, but then yesterday I noticed something peculiar. Because /home was mounted 30 times, Ubuntu started the disc-checking proces which made it switch back to the console. Now, when it tried to initialize the network, all of sudden I got a stream of information from which I could just gather that there was a kernel panic related to ndiswrapper.
Now the question is: how do I find this kernel panic back in the logs? I've checked all /var/log files and it was nowhere to be found. It's probably the wrong place to search for it, but I don't know where else to look...

---

