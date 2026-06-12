---
title: "How to slow down the internetspeed?"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by bestial on 2006-11-15
Just installed Ubuntu on my fathers laptop and everything worked out pretty well except his internet-connection. When he was on Windows we had to lower the speed to 10mbit if I don't remember wrong, because the ethernet-cable runnig from my router to his laptop is about... 20 meters so the cable doesn't handle the full speed.

But I don't have a clue how to do this in Ubuntu, I took down the laptop to my room and plugged it in with a shorter cable and that worked fine so it could only be the speed-settings that screw things up.

EDIT: To make this clearer, what I want to do is to run 10mbit full duplex on the laptop.

EDIT: Ah, now it's fixed

$ sudo ifdown eth0
$ sudo mii-tool -F 10baseT-FD eth0
$ sudo ifup eth0

that did it!

---

### Post by mips on 2006-11-15
You can try mii-tool or ethtool.

**_mii-tool:_**
Options are- 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
**sudo mii-tool -F 100baseTx-FD eth0** would set the card to 100Mb/s Full-Duplex

**_ethtool:_**
Options are-
-s DEVNAME \
                [ speed 10|100|1000 ] \
                [ duplex half|full ]    \
                [ port tp|aui|bnc|mii|fibre ] \
                [ autoneg on|off ] \
                [ phyad %d ] \
                [ xcvr internal|external ] \
                [ wol p|u|m|b|a|g|s|d... ] \
                [ sopass %x:%x:%x:%x:%x:%x ] \
                [ msglvl %d ]

[B]sudo ethtool -s eth0 speed 1000
sudo ethtool -s eth0 duplex full[/B]

---

### Post by creaturex on 2006-11-15
Umm, I'm glad you fixed it, but 20 meters of cable should have absolutely no loss at all, and should be able to run easily at full speed... Cat5e cable can function decently at lengths up to 300-330 feet (roughly 100-110 meters) so you shouldn't have any problem at all with 100BaseT and 20 meters of cable.

---

### Post by netztier on 2006-11-20
> **bestial said:**
> 20 meters so the cable doesn't handle the full speed.

Bad cable, probably not Cat5, or split pairs (not properly twisted). 20m can't really be an issue, unless your cable is unshielded and/or runs through an electromagnetically noisy environment (open Microwave, large electric motors etc). 

> **bestial said:**
> 
EDIT: To make this clearer, what I want to do is to run 10mbit full duplex on the laptop.


Running 10-FD is risky business, as in the days of 10Mbit/s hardware, it wasn't widely supported, and is often not properly autodetected.

What kind of device are you connecting to? Can you configure it? As always when playing around with manually fixing ethernet duplex settings, you **MUST** make sure that you apply the same settings to both ends of the cable (i.e NIC and switch port) . 

If you don't, chances that you end up with a duplex mismatch are >90%. Happy networking... :-/ Use a tool like netperf or iperf (from the universe repos) to test intra-LAN throughput, and you'll notice the detrimental effects an undiscovered duplex mismatch has on your throughput.

My suggestion in this situation: get a better cable and by all means leave both ends configured for auto-duplex. Chances are good that you end up with autodetected 100-FD.

regards

Marc

---

### Post by FrodoB on 2006-11-20
Your cable needs to be replaced with a good quality cat5 cable as these other folks are telling you.

---

