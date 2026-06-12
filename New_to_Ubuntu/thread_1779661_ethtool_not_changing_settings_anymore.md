---
title: "ethtool not changing settings anymore?"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by jimstolz76 on 2011-06-10
OK, I've definitely got ALL gigabit networking gear, and was even getting 600-800 Mbps throughput(measured with iperf) when I started playing with jumbo frames...

After a reboot (or update, not sure) it of course defaulted back to 100Mbps because I've never gotten around to writing a startup script for it.

I'm 99% sure I've used this exact same ethtool command before, but today it's not making changes for me.  I've got two gig NICs, but only one is connected.  Oddly enough I can't make speed changes on either of them, but I can change the autoneg setting (but then I have to reboot the machine to regain an ssh connection)

I've found quite a lot of people having this same problem, but every answer I've found ended up being that they didn't actually have gigabit network equipment. (!?!?)

Any tips on what I can look for here?

```
imac:~ Jim$ ssh root@closet
root@closet's password: 
Linux closet 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

21 packages can be updated.
16 updates are security updates.

New release 'natty' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Fri Apr 22 18:36:49 2011 from feather-mac
root@closet:~# ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: g
	Current message level: 0x00000037 (55)
	Link detected: yes
root@closet:~# ethtool -s eth0 speed 1000 duplex full autoneg on
[COLOR="Red"]******10-15 second delay after entering this command, is if it is "doing" something****[/COLOR]
root@closet:~# ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: g
	Current message level: 0x00000037 (55)
	Link detected: yes
```

---

