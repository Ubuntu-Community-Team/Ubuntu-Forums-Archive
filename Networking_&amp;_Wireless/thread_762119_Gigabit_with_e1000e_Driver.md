---
title: "Gigabit with e1000e Driver"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by Xenner on 2008-04-21
I just switched from a 10/100 switch to a 10/100/1000 switch and my ubuntu machines do not seem to run at gigabit speeds even though they have gigabit cards. My windows xp machine worked fine just plug and play.

Is there any reason these machines are still running at 100mbps??

Using the e1000e driver on a Dell Vostro 200 with a generic DHCP setup.

---

### Post by Xenner on 2008-04-23
bump

---

### Post by clarknova on 2008-04-24
> **Xenner said:**
> my ubuntu machines do not seem to run at gigabit speeds

What do you mean by that? File transfers are slow, or the interface is reporting 10 or 100 mpbs? Intel gigabit interfaces indicate their speed by the colour of the led. You can also use ```
sudo ethtool eth0
``` to see what speed and duplex your interface is reporting. This will help to determine the nature of the problem.

db

---

### Post by Xenner on 2008-04-24
it is running at 100mbps, which is what the interface and the led on both the card and the switch confirm

---

### Post by WhoCares? on 2008-04-26
Are you sure you're using a gigabit cable? If it's not a gigabit cable, link speed will always be 100 mbit.

---

### Post by clarknova on 2008-05-01
[http://en.wikipedia.org/wiki/Cat_5](http://en.wikipedia.org/wiki/Cat_5)

Cat 5, Cat 5e, and Cat 6 should all support gigabit connections.

Does ethtool report that you're using autonegotiation? It should show that autonegotiation is on and that your interface is capable of 1000baseT connections, as shown here:
```

david@micah:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbag
	Wake-on: d
	Current message level: 0x00000001 (1)
	Link detected: yes

```

You may also find useful information in the logs:
```

david@micah:~$dmesg | grep eth0
          [snip]
[70064.625411] 0000:02:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: None
[70064.625419] 0000:02:00.0: eth0: 10/100 speed: disabling TSO
[70064.627366] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[70073.477888] eth0: no IPv6 routers present

```

You may want to double-check your switch too. Do all the ports support gigabit connections? Is it set for autonegotiation (Most inexpensive switches don't allow you to change this setting).

db

---

