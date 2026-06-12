---
title: "Flapping port"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by btrotter on 2007-02-27
I am running Edgy on a Dell PC with a built-in NIC.
Most of the time it works fine, but sometimes it just goes crazy and refuses to connect to the network.

It is connected to a Cisco switch. The Cisco switch is set for autoneg.

When Ubuntu doesnt want to connect, I can look in the kern.log and see eth0 continously going up and down.

It states:
tg3: eth0: Link is down.
tg3: eth0: Link is up at 10Mbps, full duplex.
tg3: eth0: Flow control is off for TX and off for RX
tg3: eth0: Link is down.

It will do this repeatedly.

I have went to the Cisco switch and tried hard setting the speeds to 10 and 100 and the duplex to full. When I do this, the link stays down. When I go back to autoneg, it starts flapping again.

The /etc/network/interfaces file has "auto eth0" at the end.

I have tried running "sudo ethtool -s eth0 speed 100 duplex full autoneg off"
But I never see those entries get added to the /etc/network/interfaces file, and it doesnt really have any impact on the status of the link. I sometimes reboot after doing this, and still nothing.

How else can I manually set the NIC speed/duplex settings of my NIC?
What would my /etc/network/interfaces file look like if the speed and duplex was hard set?

---

### Post by btrotter on 2007-02-27
I just switched it over to another port on the Cisco switch, and Ubuntu came up. Looking at the kern.log, it shows it negotiating at 100Mbs/Full instead of 10/Full. 

I will let it run for a couple days to see if the problem is on the Cisco switch side.

---

### Post by netztier on 2007-02-27
> **btrotter said:**
> 
It states:
tg3: eth0: Link is down.
tg3: eth0: Link is up at 10Mbps, full duplex.
tg3: eth0: Flow control is off for TX and off for RX
tg3: eth0: Link is down.

It will do this repeatedly.


Hm. tg3 is a kernel module for a gigabit NIC, right? When it autonegs to 10mbps, things are bad. 10Mbps Ethernet uses different electrical signals (Manchester code) than 100Mbps (MLT3 code) Ethernet, so autosensing (speed negotiation) should be easy.

> 
I have went to the Cisco switch and tried hard setting the speeds to 10 and 100 and the duplex to full. When I do this, the link stays down. When I go back to autoneg, it starts flapping again.


Never, NEVER set only one end of a Ethernet link to full duplex. ALWAYS apply the same setting to both ends of the link, i.e. switch port AND network card. If you manually fix duplex and speed, you disable autosensing and autonegotiation - and the other end has to cope with whatever it can assume about the link - or the link stays down entirely.

I suspect that there's something wrong with the cabling, so I wouldn't go down the "fixing the duplex" road. I suggest you do this:

[LIST]
[*]set switch port and NIC to auto-speed and auto-duplex
[*]check/swap all cabling involved until 100Mbps autosensing and autonegotiation work reliably
[*]try a different switch port (as you already did) and/or a different NIC for the computer (if possible) or a different computer if necessary/needed.
[*]kernel log, **mii-tool** and/or **ethtool** will give you information about the autosense/autonegotiation process
[/LIST]

best regards

Marc


PS: come to think of it: what kind of Cisco switch is this? Is it Gigabit capable? There are some very strange things happening when both switchport and NIC want to do gigabit ethernet (because they tell each other so), while there is some 4-wire CAT5 cabling between them. Four wires are good for FastEthernet, but Gigabit needs all 8 of them. Some NIC drivers can fall back to 100 or 10Mbps, but this can take some time and link-flapping...

---

