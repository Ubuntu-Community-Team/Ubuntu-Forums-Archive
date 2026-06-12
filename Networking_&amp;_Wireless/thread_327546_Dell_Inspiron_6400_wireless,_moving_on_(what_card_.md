---
title: "Dell Inspiron 6400 wireless, moving on (what card should I buy?)"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by clconway on 2006-12-29
I've got a Dell Inspiron 6400 with the Broadcom 1390 wireless chipset. I've got the wireless working with ndiswrapper, but my setup has two features which annoy me:
[LIST]
[*]ndiswrapper and the proprietary Nvidia drivers are incompatible and cause the laptop to lock up. Without the Nvidia drivers, Suspend to RAM doesn't work.
[*]ndiswrapper and the Network Manager are incompatible. When I have Network Manager installed, Suspend to Disk stops working. (This may be a Network Manager issue, now that I think about it... Haven't looked into it.)
[/LIST]
So, basically, in order to get my wireless working, I have to give up Suspend to RAM and point-and-click WLAN management. I'm sick of this junk.

So I'm thinking about buying a new wireless card that will have better support under Edgy. The problem is I am very confused about which cards will work with my hardware.
I seem to have three choices:
[LIST=1]
[*]Replace the Broadcom card inside my laptop with something else. This is the best option, elegance-wise, but I'm not sure if there's any suitable cards on the market
[*]Get an Expresscard wireless adapter. It seems that these are rare and expensive.
[*]Get a USB adapter. I would prefer something a little less clunky.
[/LIST]
The 6400 does not have a regular PC Card slot.

Anybody have experience or recommendations that could guide me? 

Thanks, in advance,
Chris

---

### Post by themusicwave on 2006-12-29
I have an inspiron E1505 laptop with an intel pro wireless 3945 card.  I have never had problems with freezing, and automatix's wraper worked perfectly.  I am currently having issues, most likely a broken card.

If possible try moving to one of these cards.  I am still running Dapper, so I can't say if this will work with Edgy.

---

### Post by clconway on 2007-01-09
themusicwave,

My 3945 just arrived from Amazon. edgy detected it and started up the right drivers automatically ([the Ubuntu documentation]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel") seems to be out of date). The only tricky part came in clearing away the cruft from my bcm43xx install. So far, things are looking good.

Thanks!

Chris

---

