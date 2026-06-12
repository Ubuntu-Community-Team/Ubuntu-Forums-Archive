---
title: "Wake-on-LAN (WOL) on Marvell Yukon 88E8001 Gigabit NIC [Gutsy 7.10]"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by crash369 on 2008-04-20
I have been trying to get wake-on-lan to work on this computer for a couple of days now, to no avail.  I'm posting this in the hopes that someone may have a suggestion.

Here are the details and what I have tried:

lspci:
```
Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
(integrated into the ASUS mobo)
```

bios:	
```
Power Up on PCI Device = [Enabled]
Wake-Power Up On Ext. Modem = [Disabled]
```

ethtool:
```

driver: skge
version: 1.11

Supported ports: [ TP ]
Supported link modes:   10baseT/Half 10baseT/Full 
	                    100baseT/Half 100baseT/Full 
	                    1000baseT/Half 1000baseT/Full 
Supports auto-negotiation: Yes
Advertised link modes:  10baseT/Half 10baseT/Full 
	                    100baseT/Half 100baseT/Full 
	                    1000baseT/Half 1000baseT/Full 
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: pg
Wake-on: g
Current message level: 0x00000037 (55)
Link detected: yes

```

Note: most of the tutorials place this code somewhere in the startup sequence to enable WOL.
```
ethtool -s eth0 wol g
```
I did not have to do that.  Wake-on is 'g' automatically.

I have tried both to halt (`sudo halt`, `sudo shutdown -h now`) and to poweroff (`sudo shutdown -h -P now`) -- WOL does not work

I have tried changing /etc/init.d/halt from ```
halt -d -f -i $poweroff $hddown
``` to ```
halt -d -f $poweroff $hddown
``` -- WOL does not work

I have tried adding ```
ifconfig eth0 192.168.1.12 up
``` before that `halt` command in the script -- WOL does not work

I made sure that my router was letting the "magic packet" through with ```
nc -l -p 9 -u
``` and the signal came through (although it looked like gibberish to me)

I have tried WOL on WinXP, with mixed results.  WOL from 'standby' works fine.  WOL from 'hibernate' or 'shut off' does not work.

My ethernet port has 2 LEDs which are lit up when the PC is on.  When I halt ubuntu, one of them goes off, but the other remains lit.

And lastly (and I doubt this makes any difference), I have noticed that after the PC halts and powers off, when I send the magic packet, my external WD drive spins up for a few seconds before shutting off again.

Please help.  I am out of ideas. :confused:

**UPDATE:**

I have confirmed that WOL is supported and "works", by using the power button to soft-off the pc after POST.  In this case, the magic packet wakes the pc no problem.  However, shuting down from either ubuntu or winxp essentially kills WOL.

---

### Post by _SiM on 2008-07-17
Have you tried this:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=234588](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=234588)

That fixed the same problem for me :)

---

