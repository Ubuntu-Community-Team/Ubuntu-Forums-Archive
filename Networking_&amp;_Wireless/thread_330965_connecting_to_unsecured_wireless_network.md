---
title: "connecting to unsecured wireless network"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by pliu18 on 2007-01-03
hi there,

just need some help/advice on how to set up my ubuntu laptop to connect to unsecured wireless networks. as i am new migrant from xp to linux, some advice would be greatly appreciated. using my xp, the wireless wizard shows up several unsecured open connection and a simple double click gets me up and running. how do i do this in ubuntu? for example the net-ssid is uvm92 and the DHCP in windows assigns me the IP 192.168.0.9 with 192.168.0.1 being the gateway.

thanks heaps for your help.

---

### Post by c.dric on 2007-01-03
hi pliu18,

the first thing you should do is check how well your wifi card/adapter is supported in linux.

Do the following command in a terminal : 

**sudo lshw -C network**

and compare the data for your card/adapter to [the list of supported cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

Then i would recommend that you follow [this wifi how-to]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo"). It has most of the infos you need to get connected. 

You can always ask here if you get stuck somewhere. 
I hope this helps :)

---

