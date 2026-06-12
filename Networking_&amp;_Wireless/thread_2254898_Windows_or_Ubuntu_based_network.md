---
title: "Windows or Ubuntu based network?"
date: 2014-11-30
forum: Networking &amp; Wireless
---

### Post by draigcoch2 on 2014-11-30
OK I have given up on using one computer with 2 hard drives.  Currently I have:

Unit 1:   (Ubuntu 14 - 64 bit) attached by ethernet cable to the router/modem  [AMD 4 core 3.9 Gb)
Unit 2:   (Windows XP - 32 bit) with an inadequate wireless dongle.  [AMD 2 core]

When setting up a network should I base it on the Windows machine or the Ubuntu one?  
In addition what's the best way to get a good wireless connection?   What do I need to buy?

---

### Post by newbie-user on 2014-12-01
Setting up a basic network does not require any specific operating system. With that said, is your modem an actual modem or is it a combo device modem+router+wifi? If it's just a modem, then you'll need a wireless router. Almost any Linksys, Netgear, etc. will do. Then connect the modem to the WAN port of the wireless router with an ethernet cable, and then use another cable to connect your ubuntu box to one of the LAN ports on the router. Set up the wifi on the wireless router, and then connect your XP box wirelessly.

---

### Post by draigcoch2 on 2014-12-01
Thanks for the reply - here's more details:

BT Openreach router (Huawei EchoLife HG612) connected to the telephone system.  
Red ethernet cable from router  to PlusNet modem (Technicolor TG582n).
Yellow ethernet cable from modem to Ubuntu computer.
Modem has two 'buttons' on top - Wifi - WPS.

Windows computer has no external connections.  Used an old TP-Link 54m Wireless G USB Adapter to see if I could pick up a signal.  It was successful but the connection soon failed.  Presumably I need a more up-to-date link?

---

### Post by chili555 on 2014-12-01
> **draigcoch2 said:**
> Thanks for the reply - here's more details:

BT Openreach router (Huawei EchoLife HG612) connected to the telephone system.  
Red ethernet cable from router  to PlusNet modem (Technicolor TG582n).
Yellow ethernet cable from modem to Ubuntu computer.
Modem has two 'buttons' on top - Wifi - WPS.

Windows computer has no external connections.  Used an old TP-Link 54m Wireless G USB Adapter to see if I could pick up a signal.  It was successful but the connection soon failed.  Presumably I need a more up-to-date link?I'm not quite sure I understand what the Huawei is doing for you that the Technicolor doesn't do. I believe the Technicolor is a DSL modem and a router and has wireless capabilities and has two ethernet ports. No?

I think I'd hook the Technicolor to the DSL phone line and be done. Of course, I am not very familiar with the BT system there. Perhaps they require that only BT provided equipment be connected first in line. And by 'provided,' I suspect that means leased at a high cost buried in the cost of the service. 

I suspect you can configure the modem from the ethernet connection and then be all set.> Setting up a basic network does not require any specific operating system. Quite correct. I have or have had at times, Windows, Linux and iOS systems connected with no issues whatever.

I do suggest that the wireless use WPA2-AES encryption and a powerful password.

---

