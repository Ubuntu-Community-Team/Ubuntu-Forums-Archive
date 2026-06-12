---
title: "WMP54GS not recognized"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by whiteline on 2007-01-25
I installed ndis-gtk using system->administration->synaptic package manager. I got my wmp54gs cd out and searched through drivers till i found wmp45gs.inf copied that to the desktop and then using that i went to system->administration->wireless network drivers and loaded the wmp54gsa.inf file but it said that the hardware wasn't in place. After hours of searching, reading taking out and putting back in nothing happened. Please if anybody could help assist me in my problem i would greatly appreciate it. 
Sincerely, 
whiteline 

ps- i've tried to remove the card, install it and then put the card back in.. Nothing happens.

---

### Post by Jimmey on 2007-01-26
Try here.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy?highlight=%28bcm43xx%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy?highlight=%28bcm43xx%29)

---

### Post by serpentine on 2007-02-02
I'm running Edgy and I downloaded the latest stable ndiswrapper package from sourceforge and compiled.  That worked for me.  Couldn't get the ubuntu versions to work for me.

I didn't see the how-to that jimmey points out.  So I will check that out also.  Looks like a good alternative.  Thanks jimmey!

---

