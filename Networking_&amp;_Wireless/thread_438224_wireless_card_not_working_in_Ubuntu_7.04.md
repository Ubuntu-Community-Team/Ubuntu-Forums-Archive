---
title: "wireless card not working in Ubuntu 7.04"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by carlosmb on 2007-05-09
Hi everybody!!

Ok here is what is happening to me...I upgraded to 7.04 and it seen that my wireless card is not recognized for the new version. I uninstall the 7.04 and I go back to 6 and it is recognized right away. 
In network menu it is even not displaying wireless connection in 7.04.I would hate to go back to the older versio n because of this problem. Did somebody have the same problem? my wireless card is in the list of "good ones" for Ubuntu....

any help will be very appreciated.


Thanks!!!!

---

### Post by superyounan1 on 2007-05-09
I compiled drivers for my wireless card in edgy, but when i tried it in Fiesty they didnt work - on the flip side, ndiswrapper worked in fiesty when it didnt in edgy, and for some weird reason performance was better with the ndiswrapper.

did you try that?

---

### Post by Blacktalon on 2007-05-09
What type of card do you have?

That should be the first thing you should let people know, cuase there are a lot of cards out there and different ways to configure and install them.

But I am going to assume you are using a generic card.  Ok, without any information, I can suggest that you go to your network manager and enable your card.


Again, please post more detail on the problem, what you have tried, what card you use, and etc.

---

### Post by carlosmb on 2007-05-09
> **superyounan1 said:**
> I compiled drivers for my wireless card in edgy, but when i tried it in Fiesty they didnt work - on the flip side, ndiswrapper worked in fiesty when it didnt in edgy, and for some weird reason performance was better with the ndiswrapper.

did you try that?


I am going to do that. I thought that if worked with edgy...it should work with Fiesty...let me try ndiswrapper  and let's see....

thanks so much for your help!!!

---

### Post by carlosmb on 2007-05-09
> **Blacktalon said:**
> What type of card do you have?

That should be the first thing you should let people know, cuase there are a lot of cards out there and different ways to configure and install them.

But I am going to assume you are using a generic card.  Ok, without any information, I can suggest that you go to your network manager and enable your card.


Again, please post more detail on the problem, what you have tried, what card you use, and etc.


Thanks for your quick response. I have a DLink, I am not remembering the number know...I am at work..;-)but I will try what you said and even restart the router.....

Thanks!!

---

### Post by stchman on 2007-05-09
> **carlosmb said:**
> Thanks for your quick response. I have a DLink, I am not remembering the number know...I am at work..;-)but I will try what you said and even restart the router.....

Thanks!!

Give us an lspci.  Dlink has different chipsets for the same card model.  Is it Atheros, TI, Boradcom, etc?

---

### Post by Aoimoku on 2007-08-13
I am having the same problem.  I have a D-Link wireless card:
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc D-link DWL-G650 (Rev B3,B5) Wireless cardbus adapter
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 24000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

I know the ssid needed to access wireless.  I won't be able to test anything out until I arrive back at college, which will be on Sunday (8-19-07), but any help would be greatly appreciated.  I will reply back if it works or not on Sunday evening.

The restricted driver manager shows that the Atheros Hardware Access Layer is enabled and in use.  I may be a computer science major, but I cringe everytime I have to compile something, so be gentle with the suggestions.
This card was working in ubuntu 6.10, but not again since the 7.04 upgrade.

I have the Wifi-radar program installed in Gnome.

Thanks for any help.

---

