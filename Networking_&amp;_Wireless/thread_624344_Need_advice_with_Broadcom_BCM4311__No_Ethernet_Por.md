---
title: "Need advice with Broadcom BCM4311 / No Ethernet Port"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by agentpink on 2007-11-26
I'm unable to update my network card driver using ndiswrapper or bcm43xx. I've tried following all the tutorials I can find, but all of them require me at some point to connect to a LAN line and run a update command in the terminal. 

My laptop has no build-in ethernet port, and because of this I'm experiencing extreme frustration.

 I do have a USB flash memory drive, and would appreciate if someone out there can guide me step-by-step on what I have to do to transfer an updated file from my pc computer (windows xp) to my laptop (Ubuntu 7.10) using the USB flash memory.
 

My network card is a Broadcom BCM4311. HELP ME PLZ! :confused:

---

### Post by mellowd on 2007-11-27
If you want to copy a file from your windows xp system to your ubuntu system using the flash memory its pretty easy. Put the flash into your windows xp machine, copy the file onto it. Then stick the flash drive in your linux box and copy it over

---

### Post by agentpink on 2007-11-27
> **mellowd said:**
> If you want to copy a file from your windows xp system to your ubuntu system using the flash memory its pretty easy. Put the flash into your windows xp machine, copy the file onto it. Then stick the flash drive in your linux box and copy it over

What about the update file? Where do I acquire that from?

---

### Post by mellowd on 2007-11-28
You said it was on your windows xp pc?

---

### Post by agentpink on 2007-11-28
> **mellowd said:**
> You said it was on your windows xp pc?

No. I have Ubuntu 7.10 successful installed on my laptop. My issue is with my WLAN network card (Broadcom BCM4311). 

I've tried using both ndiswrapper and bcm43xx, to make my WLAN card correspond with my copy of Ubuntu.  Unfortunely, during a process I'm required to be connected to the internet through a direct LAN line for an update. 

My laptop has no Ethernet ports, therefore I cannot update certain files. My question is, where can I find these files that will update my network card? And in the terminal what should I do?

---

### Post by mellowd on 2007-11-29
This was your original question:

> **agentpink said:**
> 
 I do have a USB flash memory drive, and would appreciate if someone out there can guide me step-by-step on what I have to do to transfer an updated file from my pc computer (windows xp) to my laptop (Ubuntu 7.10) using the USB flash memory.
 


Now you say that's not the case?

Surely the script that wants you to connect to the internet should be able to connect via the wlan card. In fact the process shouldn't care which connection to use as long as it can get out to the internet

---

