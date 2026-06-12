---
title: "ASUS Z97-A LGA 1150 Intel Z97 Wired LAN connection running at 100 instead of gigabit"
date: 2015-11-06
forum: Networking &amp; Wireless
---

### Post by onesojourner on 2015-11-06
I would like to take full advantage my network. I tried manually changing it with:

```
sudo ethtool -s eth0 speed 1000 duplex full
```\

That just broke my connections. Does any one have any thoughts and what might be the issue? This setup is full speed if I boot a windows hdd.


```
Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: on (auto)
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes

```

---

### Post by gordintoronto on 2015-11-07
What is the brand and model of your router?

---

### Post by oldfred on 2015-11-07
My Asus-AR which is identical to yours except for video ports shows this from the wireless-info.txt file, which I ran even though no wireless:


```
nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | e1000e | connected | yes     | 1000 Mb/s |              | <MAC eth0>

```

---

### Post by onesojourner on 2015-11-07
> **gordintoronto said:**
> What is the brand and model of your router?

Switch: HP Procurve 1810G-8
DHCP Server Buffalo Airstation running dd-wrt (I do not have the model in front of me right now)

---

### Post by gordintoronto on 2015-11-08
That switch only has one gigabit port, is that the one you are plugged into?

---

### Post by onesojourner on 2015-11-11
> **gordintoronto said:**
> That switch only has one gigabit port, is that the one you are plugged into?

Negative. It is a full gigabit switch. Like I said If I boot to a windows drive it runs at gigabit speeds. I have also tested [THIS CARD]("http://www.amazon.com/gp/product/B001CY0P7G?psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00") and everything runs at gigabit speeds.

---

### Post by onesojourner on 2015-11-11
Here is the switch admin page with several of my other devices running at full speed.

[IMG]http://i.imgur.com/1RuuQp7.jpg[/IMG]

---

