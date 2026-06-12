---
title: "Reboot to reach internet if modem/router wasn't already connected at boot"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by lucascury on 2007-08-12
Hi guys! I've been having problem with my connection to the internet since I've installed Ubuntu here. My version is 7.04, just for you to know. Anyway, what happens is that I use a modem/router, model Alcatel/Thomsom SpeedTouch 510, and it's configured to ppoe, so it connects to the internet itself. If I turn on the modem after Ubuntu have booted, Ubuntu doesn't recognize the connection. The NetworkMaganer even says I'm now connected to a wired network, but nothing works, though.

I've seen some threads here and I've tested several things. It's not a DNS problem because I can't ping anything and I've already tried putting my ISP's DNS there. It's not a gateway problem because I've tried to put the modem's IP as gateway and it didn't work. Finally, I've tried to ping/connect to modem firmware, and it didn't work too.

I've tried once disconnecting and reconnecting while logged on on Ubuntu and it worked fine after modem/router rebooted.

I suspect the network card isn't even started when the internet is not connected before booting, even though the NetworkManager says it's all ok and working. Anyone's got any idea? It's a lot boring to see I've forgotten to start the modem and to reboot (logging off and on doesn't work).

Thank you,
Lucas

---

