---
title: "Internet Question"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by ART_Adventures on 2006-10-14
I have two separate internet connections each via a ethernet cable. In Windows, if I swap any one of the cables into the ethernet port I get an internet connection which works.

However, in Ubuntu, one of the cables works and the other doesn't. Does anybody know why?

Thanks for the help.

---

### Post by NeoLithium on 2006-10-14
There could be a couple of things that might be the culprit. Do you see all the proper devices with ifconfig?   You may have to activate and load the device/connection on boot; depending on what type of connection that you have to your ISP...

---

### Post by ART_Adventures on 2006-10-14
Thanks for the reply. Both seem to work now via wires. My ultimate aim is to connect to each of these wirelssly. Windows can connect to both wirelessly. One connection is WEP and the other is WPA. Ubuntu, however, can only connect wirelessly to the WEP connection.

I've downloaded WIFI Radar and Network Manager. I have a Netgear WIFI card (driver: WG511v2) which I use through ndiswrapper. I managed to connect to the WEP connection via WIFi-Radar. But the WPA connection doesn't seem to work.

I'm not sure if there's a "real problem" or if it's me getting the settings wrong. I know the ESSID, the WPA key and the broadcast channel. WIFI-RADAR asks me for other things, though- like WPA driver and such. I don't know what to put for these. The error WIFI-Radar gives me is something like "Cannot Acquire IP Address".

Can anybody help? Thanks.

---

