---
title: "Help removing dell 1390"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by kingbree on 2007-09-13
Hi, 
  I'm at the end of my wits right now. i Haven't got this wifi working after a few days of trying, For some reason my  $lspci etc  thinks I have a broadcom dell 1390 wifi card installled I'm not so sure,  as I have a HP/Compaq machine, and this 1390 only started getting mentioned after I ran  the automated install script on this forum.
I've gotten driver's from the Compaq/HP site(albeit Vista drivers) and ran through the ndiswrapper and fwcutter installation instructions about a million times. however I would be more confident in the results if I could return the wifi network card to being unknown before I start out. 
Or can some one at least where can I find out what components are in my machine.(Compaq c504ea).

Please help me I am loosing my mind.

---

### Post by kevdog on 2007-09-13
Im not sure what to tell you but the dell true mobile mini pc card is a very common component and is found in many other brands except Dell.  Ive seen them mentioned in compaq machines in this forum before.  Whatever the brand, it has a broadcom chipset.

---

### Post by kingbree on 2007-09-13
I get you I just think that it might be a different card because there are no XP drivers available for this machine, the drivers I got from the HP site, contain bcmwl6.inf etc, not bcmwl5 like everybody else seems to get. 
I know this is a panic post (funny how they tend to clear your mind), but  looking at it again, I think I need to get hold of the wl_aspsta.o file  for this specific machine, now, would that be in the driver.exe? exactly where does it come from?

---

### Post by kevdog on 2007-09-13
bcmwl6 = broadcom wireless version 6,  its the newer version as compare to version version 5

you could use this in conjuction w ndiswrapper or use the bcmcutter approach w wl_apsta

---

### Post by kingbree on 2007-09-13
:) Ok, but the hardware report says that the 1390 is a Mini-PCI card, and the port it is in an express PCI port, together with the fact that I cant find XP drivers leads me to think that i have a newer card than the 1390? 
Is it possible to return the system to believing it has no information about the card at all?

---

