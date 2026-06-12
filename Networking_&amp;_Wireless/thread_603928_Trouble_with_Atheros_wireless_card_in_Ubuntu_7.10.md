---
title: "Trouble with Atheros wireless card in Ubuntu 7.10"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by igarg1 on 2007-11-05
I am running Ubuntu 7.10 (dual boot option with Windows XP) on a Toshiba Satellite A75 notebook. I have an Atheros wireless card and a Belkin router. I can "see" my network but when I try connecting by putting in the passphrase it won't connect. The wireless connection works ok with the windows. Any ideas as to what the problem might be or where to start looking?

---

### Post by spd106 on 2007-11-06
Are you using roaming mode (nm-applet) or static (network-admin)?

What kind of encryption are you using, WEP, WPA1-PSK etc?

I've had intermittent trouble on WPA1 with CCMP/AES, so I recommend using TKIP.

---

### Post by Astrofreak85 on 2007-11-09
I've got exactly the same problem here, but I'm using a Desktop machine with a D-Link card (Chipset 5212/5213)

I tried NDISwrappe, but this also didn't work...I can remember this card workt out of the box with 6.06 and 6.10, but not with Gutsy
I see the neworks but can't conect to them, even if they are open.

Maybe someone can help here...

Thanks,
Astro

---

### Post by jfairy on 2007-11-09
Yeah I just had to buy a new pcmcia card this week to get around the fact my other Netgear card wouldnt go in Gutsy.
Got a D-Link G-650, has the same chipset you are talking about - Atheros 5212, I didnt have to go near ndiswrapper, worked pretty much straight out of the box, it auto-detected, went through network settings, un-enabled roaming & set up a WEP (yeah I know but it works for me).
Restricted Drivers Manager shows that the Atheros Hardware Layer (HAL) is enabled & in use (happy happy joy joy). 
Sorry this isnt much help to you, just another story. 
Apologies of any of these questions are asking the bleeding obvious: 
Are you sure it is the passphrase you are being asked for & not the actual key, ie have you tried entering the letter/number code?
Im assuming your router is open because Win can connect....

---

### Post by Astrofreak85 on 2007-11-09
I've tried something:

I guesed it could be a problem with the kernel or something, so I tried to install "linux-rt", 
and suprise: there it works, but system is real slow with this kernel on my machine

now I'm in doupt if it's the kernel itself that wronk, or the driver

Is there an giude how to selfcompile and install the latest madwifi (create dep packets) anywere? 

-- Astro

---

