---
title: "eth1 [wireless] configuration gone upon feisty upgrade"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by lvijay on 2007-04-30
I recently upgraded from Edgy to Feisty and I've been having networking problems since.

It used to be that my networking manager would automatically connect to my wireless university connection through dhcp and failing that, I would $ sudo ifup eth1 and $ sudo ifdown eth1 as necessary.  When I was connecting to a secure network, I'd $ sudo ifconfig eth1 essid <whatever> key <something> rate auto and so on.

After my upgrade, saying

$ sudo ifdown eth1

gives the following error:

ifdown: interface eth1 not configured

It does connect to the wireless network but when something goes wrong, I have to restart the computer to get it working again.

My NetworkMonitor works though.  It shows the signal strength for eth1 correctly.

Any suggestions welcome.  Preferably one that involves changing files and giving me control through the terminal.

I'm on a Dell Inspiron 630m with an Intel Pro Wireless 2200 802.11 b/g card.

Thanks
Vijay

---

