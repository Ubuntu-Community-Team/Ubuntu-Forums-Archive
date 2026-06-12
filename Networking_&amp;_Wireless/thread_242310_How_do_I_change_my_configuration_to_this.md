---
title: "How do I change my configuration to this?"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by mengfei on 2006-08-23
Hi there!
I need to change my configuration to this in Ubuntu.

I already did this in Windows, and thus rendered my connection to my router useless (on wireless now).

So, since Ubuntu is still able to use my ethernet cable to connect to the router, I took it that it doesn't have these configurations.

How would I go about doing so, so that I may be able to use the Ethernet ports in my Penn State dorm?

Configuration Information --
   IP Address:           66.71.59.175
   Subnet Mask:          255.255.255.0
   Default Gateway:      66.71.59.1
   Host Name:            JZL5104
   Domain:               RH.PSU.EDU          
   Primary DNS Server:   128.118.25.3
   Secondary DNS Server: 130.203.1.4

---

### Post by majesticturkey on 2006-08-23
I'm over here at the much-better Ohio State University (;)) and just plugged my ethernet cable into the wall. One end in the wall, one end in my computer, boot up, I have internet. So there shouldn't have to be any configuration...

---

### Post by mengfei on 2006-08-23
Oh, haha, well that would explain why Ohio State is much-better, hahaha.

Pennstate has this annoying thing where you have to register your ethernet card's address, and then reconfigure your IP settings for them.

Why? Because they monitor your bandwidth. A lousy 1.5gb upload and download each for every week!!!!!!!!!!!

GRAGRAGHARHGHARGH

so how would I go about putting those settings in? Haha

---

### Post by NetworkGuy on 2006-08-23
You should be able to enter all those settings using System --> Administration --> Networking

Find your Ethernet card (usually ETH0), click on it and then click on properties.  Set you IP address, subnet and gateway here.  Go back to the general and DNS tabsl and enter the remaining of the informtion.

You should be good from there.

---

