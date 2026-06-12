---
title: "WLAN - compatibility question"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by christian8287 on 2005-11-09
Hi!

I want to buy a new WLAN PCMCIA card. 

I have heard about good compatibility to Atheros chipset. Somebody wrote, that it worked immediately.

Do you know other chipset working well under Ubuntu?

Here are some cards. Please write me, if you have experience with one card listed below:

[LIST]LevelOne WPC-0300
Netgear WAG511
Netgear WG511T
SMC 2336W-AG
Netzwerkkarte, PCMCIA, 54Mbit wireless, Conceptronic C54C/RC, WLAN
D-Link AirPlus G DWL-G630, 54Mbps, CardBus
D-Link AirPlusG+ DWL-G650+, 54Mbps, Cardbus
D-Link AirPlusXtremeG DWL-G650, 108Mbps, CardBus
Longshine LCS-8531G2 54Mbps Wireless Netzwerkkarte PCMCIA[/LIST]

If you know other cards, working immediately under Ubuntu, please contact me. Please also contact me, if you know other chipsets working well with ubuntu and without ndiswrapper.

Thank you in advance!

regards,
Christian.

---

### Post by Lambert on 2005-11-09
I'm using a dwl-g650. Worked out of box on breezy for me. I tried using wpa instead of wep though and couldn't get it working but wep is secure enough for my usage.

A good source for other cards and users experience is [[COLOR="Blue"]here[/COLOR]]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28WIRELESS%29")

---

### Post by dcroal on 2005-11-09
My SCMWCBT-G [http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=5&scid=&pid=1447](http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=5&scid=&pid=1447) works with both madwifi and ndiswrapper. I can recommend this card.

I prefer the madwifi driver as it seems more stable and also because the ndiswrapper config does not seem to like to come up on boot.

Dave

---

