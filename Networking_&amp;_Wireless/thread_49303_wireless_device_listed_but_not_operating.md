---
title: "wireless device listed but not operating"
date: 2005-07-15
forum: Networking &amp; Wireless
---

### Post by SBOldMan on 2005-07-15
I've got a fresh install and I see my wireless PCMCIA card listed in the Control Panel.  When I look in the Network Settings area, my wireless card is not listed in there.  Is there something I need to do in order to activate it or something?  I was first looking at using ndiswrapper, but since I see it recognized I thought maybe I wouldn't need it.  Am I mistaken?  Thanks!

---

### Post by stevenyu on 2005-07-15
if you type in **iwconifg** (assume you have wireless tools utility package installed) in the terminal, what does it shows?

---

### Post by SBOldMan on 2005-07-16
[QUOTE=stevenyu]if you type in **iwconifg** (assume you have wireless tools utility package installed) in the terminal, what does it shows?[/QUOTE]

Thank you for the reply steven!

iwconfig replies with -

lo          no wireless extensions
eth0      no wireless extensions
sit0       no wireless extensions

This is a Motorola WN825G PCMCIA card.

---

### Post by stevenyu on 2005-07-17
so there is no wlan0 :-(

have a look at the dmesg and see if there is any error message regarding to the loading of the driver module for your wifi.

have you try using the ndiswrapper to load the windows driver?

---

### Post by SBOldMan on 2005-07-17
[QUOTE=stevenyu]

have you try using the ndiswrapper to load the windows driver?[/QUOTE]

That is what I was going to try, but hoped that since I could see the card listed in the Device Manager that I would not need to.

I'll go try to wade thru some of the ndiswrapper stuff and see if I can get it to work. 

Thanks.

---

