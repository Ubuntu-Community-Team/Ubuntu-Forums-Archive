---
title: "Gigabit NIC connects to 100Mbit switch but not to 1000Mbit switch ??"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by richo132 on 2008-03-03
When connected to a 100Mbit switch (Linksys SD208 ) my Linksys eg1032v3 NIC is correctly detected and apparently works properly with either the r8169 or eg1032v3 driver.
If I connect the NIC directly to a 1000Mbit switch (Linksys SD2008 ) the NIC doesn't work.
When connected to the 1000Mbit switch, a LED on the NIC lights up on a cold boot, but goes out when boot reaches the udev stage.
If the NIC is connected to the 1000Mbit switch via the 100Mbit switch, everything works fine.
In other words:
network > 1000Mbit SW > 100 Mbit SW > eg1032v3 eg1032v3 works fine
network > 1000Mbit SW > eg1032v3 eg1032v3 doesn't work
As far as I can tell the 2 switches perform correctly with other attached devices.
I am using Cat 6 cables.
When attached to 1000Mbit SW and rebooted, the PC correctly identifies the NIC, maps it to eth0 and loads the driver. However, eth0 does not come up.
Any suggestions on how to fix or further diagnose this problem ?
(previously posted in error on Hardware & Laptops)

---

### Post by netztier on 2008-03-04
> **richo132 said:**
> 
I am using Cat 6 cables.


Are you certain that these are in good working order? i.e. have all 8 wires in them, all four pairs properly twisted and no cable breaks? 1000baseT needs all four twisted pairs, 100Mbit will work with two pairs. Gigabit NICs and switch ports will detect missling links in a cable and can fall back to 100Mbit when needed - though not all combitations of BIOS, driver and switch port are capable of this.

What are the outputs of **sudo mii-diag -vv eth0** and/or **sudo ethtool eth0**? 

regards

Marc

---

### Post by richo132 on 2008-03-04
Marc, thanks for your interest and assistance with my problem.
The cables I'm using are new Belkin parts, but I will test them when I remember where I put my cable tester :confused: 
In the meantime, results of commands you suggested:
(NB the eg1032v3 driver does not support these commands.)

**Connected to 100Mbit switch using r8169 driver**
root@xtunes:~# ethtool eth0
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
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

root@xtunes:~# mii-diag -vv eth0
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
  Using the new SIOCGMIIPHY value on PHY 32 (BMCR 0x0000).
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Your link partner advertised 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-    FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #32 transceiver registers:
   1000 796d 001c c910 0de1 45e1 0005 2001
   45e1 0300 0000 1000 1007 f880 0000 3000
   0060 6c40 0000 2f40 0060 0002 8fe1 0108
   2740 2700 0000 011e 8420 0000 0000 a8e0.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 Basic mode status register 0x796d ... 796d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Vendor ID is 00:07:32:--:--:--, model 17 rev. 0.
   No specific information is known about this transceiver type.
 I'm advertising 0de1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD     10baseT.
   Negotiation  completed.

**Connected to 1000Mbit switch using r8169 driver:**
root@xtunes:~# ethtool eth0
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
	Duplex: Half
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: no

root@xtunes:~# mii-diag -vv eth0
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
  Using the new SIOCGMIIPHY value on PHY 32 (BMCR 0x0000).
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 Basic mode status register 0x7949 ... 7949.
   Link status: not established.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Your link partner advertised c5e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #32 transceiver registers:
   1000 7949 001c c910 0de1 c5e1 000d 2001
   e808 0300 0000 1000 1007 f880 0000 3000
   0060 7000 0000 2040 0060 0000 0098 0108
   2740 2700 0000 0800 8420 0000 0000 0870.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 Basic mode status register 0x7949 ... 7949.
   Link status: not established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Vendor ID is 00:07:32:--:--:--, model 17 rev. 0.
   No specific information is known about this transceiver type.
 I'm advertising 0de1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is c5e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Negotiation  completed.

---

### Post by netztier on 2008-03-04
> **richo132 said:**
> 
In the meantime, results of commands you suggested:
(NB the eg1032v3 driver does not support these commands.)


From what I was able to gather about this NIC, you should be using the r8169 driver anyway. (*sigh* another Realtek nightmare).

Another thing: please use the CODE-Tag when inserting console output (using the # sign from the formatting toolbar)- it makes your post a lot more readable. I took the liberty of adding them in the reply here.

> 
**Connected to 100Mbit switch using r8169 driver**
```
root@xtunes:~# ethtool eth0
Settings for eth0:
..
..

```


Looks all very normal to me. Now let's look what happens in the next case.

> **Connected to 1000Mbit switch using r8169 driver:**
```
root@xtunes:~# ethtool eth0
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
[COLOR="Red"]	Speed: 100Mb/s
	Duplex: Half[/COLOR]
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: no

root@xtunes:~# mii-diag -vv eth0
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
  Using the new SIOCGMIIPHY value on PHY 32 (BMCR 0x0000).
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 Basic mode status register 0x7949 ... 7949.
   Link status: not established.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
[COLOR="Red"] Your link partner advertised c5e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
[/COLOR]   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #32 transceiver registers:
   1000 7949 001c c910 0de1 c5e1 000d 2001
   e808 0300 0000 1000 1007 f880 0000 3000
   0060 7000 0000 2040 0060 0000 0098 0108
   2740 2700 0000 0800 8420 0000 0000 0870.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 Basic mode status register 0x7949 ... 7949.
   Link status: not established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Vendor ID is 00:07:32:--:--:--, model 17 rev. 0.
   No specific information is known about this transceiver type.
 I'm advertising 0de1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
[COLOR="Red"] Link partner capability is c5e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Negotiation  completed.[/COLOR]
```


Something's fishy. The peer device at the other end of the cable does not advertise 1000baseT capabilities. This somehow stinks of a switch port in fixed speed and duplex configuration, which almost always results in a NIC defaulting back to half duplex operation and the nuisance of a duplex mismatch.

In this case however, it seems to lead to a nonworking link. If possible, have that gigabit switch port properly configured for autospeed/auto-duplex. In these days, fiddling around with fixed speed and duplex settings is a case for paranoid administrators or ethernet hardware from yesteryear exclusively.

Can you get the thing working at 100mbps on the gigabit switch if you limit the NIC to 100Mbps with either ethtool or by adding a parameter to /etc/network/interfaces?

regards

Marc

---

### Post by richo132 on 2008-03-04
Marc,
Thanks again for your comments.
I found my cable tester and all involved cables tested good on all four pairs.
The 1000Mbit switch is a Linksys SD2008 - unmanaged and supposedly auto everything.
There doesn't seem to be any option for configuring the ports.

While I was trying to get a connection happening @ 100Mbits on a 1000Mbits switch, I plugged in my  other SD2008 to make it easier to access physical ports. After a short while the LEDs on the NIC lit up.
This happened just after I entered the command "modconf" - I think this was a coincidence. The modconf module was not installed and I was shown a message on installing it with apt-get.

So, this config works:
network > 1000Mbit SW-A > 1000Mbit SW-B > eg1032v3
but this does not:
network > 1000Mbit SW-A > eg1032v3

Barring any faults, the only difference I can see between SW-A and SW-B is that SW-A has a mixed load of 100Mbit and 1000Mbit connections whereas SW-B only has two 1000Mbit connections.
The port on SW-A that would not support a direct connection to the eg1032v3 NIC,
was happy to do so when the connection went via SW-B.    

Anyway, attached output confirms a successful connection when both switches are in play.
NB:
ethtool claims connection is @ 1000Mbit full duplex
mii-diag -vv eth0 reports 100baseTx-FD 
- so I'm not sure what the actual connection speed is.

```
root@xtunes:~# ethtool eth0
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
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

```

```
root@xtunes:~# mii-diag -vv eth0
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
  Using the new SIOCGMIIPHY value on PHY 32 (BMCR 0x0000).
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Your link partner advertised c5e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
 MII PHY #32 transceiver registers:
   1000 796d 001c c910 0de1 c5e1 000d 2001
   4f89 0300 3800 1000 1007 f880 0000 3000
   0060 acc0 0000 0100 0060 0000 ef84 0108
   2740 0010 0000 0105 0910 0000 0000 98e0.
 Basic mode control register 0x1000: Auto-negotiation enabled.
 Basic mode status register 0x796d ... 796d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Vendor ID is 00:07:32:--:--:--, model 17 rev. 0.
   No specific information is known about this transceiver type.
 I'm advertising 0de1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is c5e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Negotiation  completed.

```

---

