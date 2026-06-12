---
title: "Can't connect to WPA network"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by Revenant86 on 2008-03-11
I have a Broadcom 4318 Airforce one chip in my laptop and I cannot connect to a wpa protected network. I am using ndiswrapper for the drivers and wicd and I can connect to an unprotected network. Also, when I try to connect to my network WICD says None:Obtaining IP address instead of network name:Obtaining IP address.

---

### Post by eebagum on 2008-03-11
I had problems setting up my card. I didn't have much luck with Wicd. I'm running Ubuntu 7.10 which seems to have the drivers but you need to go into: System>Administration>Restricted Drivers Manager. It will probably have: Firmware for Broadcom 43xx chipset family   'Not in use'. I ticked the box to enable it and had to install
'bcm43xx-fwcutter_006-3'. Before doing anything, there is a post for the correct procedure around 4 days ago, if you do a forum search on bcm43xx it should hopefully get you there. Not going to try and talk you through it as I'm new to this myself. 
I'm not using Ndiswrapper or Wicd, i just enabled the firmware with fwcutter, enabled roaming because unticking it caused me loss of network setup gui.s. I'm using Wpa with Tkip and haven't had a problem. Happy hunting, if I find the post i'll get back to you.

---

### Post by eebagum on 2008-03-11
**This post could be related to an Ubuntu bug filed at**: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This might help

---

### Post by handydan918 on 2008-03-11
If you have spaces in your passphrase, that can cause problems.

---

### Post by Revenant86 on 2008-03-11
I don't have spaces in my passphrase and I tried the firmware cutter stuff before ndiswrapper and that didn't work either.

---

### Post by Revenant86 on 2008-03-11
It works! I tried the acerlaptop-wifi that is linked in the wiki page you linked to, Eebagum, and it worked. Which is weird because I have a Compaq, not an Acer, but it does say that page that it may help other laptops.

---

### Post by eebagum on 2008-03-12
Nice one, it's probably something to do with the way the chip's driven by the manufacturer.
It may be worthwhile marking this thread as solved so others can benefit. believe it or not there's a thread on how to mark a thread 'Solved' in this forum.(a page or 2 back or forward, I can't remember!).:cool:

---

### Post by krazyd on 2008-03-12
Hi Revenant86, just FYI I also have the 4318 chip, and am currently running Hardy alpha6. The b43 driver has reached a new level of maturity - it is now rock solid and works as well as on WinXP. 

If I never have to install ndiswrapper again, it will be too soon! :D

---

### Post by Monstroxus on 2008-03-12
I had a similar issue... I could connect to an unprotected wireless network, but not to WEP/WAP. I uninstalled NDISWRAPPER and BCM43xxx cutter, uninstalled WICD/Networkmanager, reinstalled BCM43xxx cutter and set it up. (all the while using wired connection) Then reinstalled Networkmanager, and now it works. Make sure the nothing relevant is blacklisted. (some tuturials I had been messing with put a lot of blacklists for bcmcutter, I unblacklisted them)

Anyway, I was soooo happy and proud that I fixed it now! It gave a kick! haha... hope the above info might be of help.

---

