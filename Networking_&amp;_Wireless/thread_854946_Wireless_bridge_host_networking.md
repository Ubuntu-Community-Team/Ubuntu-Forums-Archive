---
title: "Wireless bridge host networking"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by nozomiyume on 2008-07-10
So I recently installed Hardy on my Dell XPS 1710, which has an ethernet connection as well as a wireless card. I also quickly installed VirtualBox and WinXP in that (which I need for work). 

I got the ethernet connection setup in host mode going through the following script: 

```

#!/bin/bash

USER=vthakkar
BRIDGE=br0
TUNDEVICE=tap1
LANDEVICE=eth0

sudo tunctl -t tap1 -u $USER
sudo chown root.vboxusers /dev/net/tun 
sudo chmod g+rw /dev/net/tun 

sudo brctl addbr $BRIDGE

sudo ifconfig $LANDEVICE 0.0.0.0 promisc 
sudo brctl addif $BRIDGE $LANDEVICE

sudo dhclient $BRIDGE 

sudo brctl addif $BRIDGE $TUNDEVICE
sudo ifconfig $TUNDEVICE up 

```

Now I'm struggling quite a bit to get the wireless host mode working. I need both to work (in different situations) as I need the wired connection in host mode for work, and a wireless connection in host mode for home. The only tutorials I've seen after googling around a lot have been static IP with parprouted - is there any way at all to do this via DHCP? It seems at the worst you could get Ubuntu to act as a router and have the network adapter passed to virtual box connect to that. 

Can anyone help me with this? I've been wrestling with it for some time and would love to get it working :confused:

---

