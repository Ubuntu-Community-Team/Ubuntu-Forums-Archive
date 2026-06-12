---
title: "internet connection problem"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Taninim on 2008-09-24
Hi

I can connect to the net but I get a "address not found" massage for ~50% of the pages I surf to. When I refresh it usually helps but it is very annoying to surf like that. it is the same when I am using FireFox and Konquerer other net programs work well (skype, azureus, nicotine). When switch to windows it is working properly.

 
I am using a Motorola sb5100 modem connected to a usb.
And I am connection with a script that looks like that:


#!/bin/bash

USERNAME="my username"
IFACE=eth1
PPTPS=pns.barak.net.il
NEWDNS=212.150.49.10

ifdown $IFACE
ifup $IFACE

	NVGW=$(ping -c 3 -w 3 $PPTPS | head -n 1 | cut -d" " -f3 | cut -d"(" -f2 | cut -d")" -f1)
	CABLEGW=$(route -n | grep 0.0.0.0 | cut -d" " -f10 | tail -1)
	
route add -host $NVGW gw $CABLEGW dev $IFACE

pptp $NVGW debug user $USERNAME mtu 1380 mru 1380 defaultroute persist nobsdcomp usepeerdns

sleep 6

	NEWGW=$(ifconfig ppp0 | grep inet | cut -d":" -f3 | tail -1 | cut -d" " -f1)

route add default gw $NEWGW
route del default gw $CABLEGW

echo nameserver $NEWDNS > /etc/resolv.conf

---

