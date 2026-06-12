---
title: "[Ubuntu 14.04] Ethernet wire is not recognized (1Gbit/s connection)"
date: 2014-12-16
forum: Networking &amp; Wireless
---

### Post by maxoudela on 2014-12-16
Hi all,

I'm currently under Ubuntu 14.04. I recently got a new internet connection at home which deliver 1Gbit/s of data. So I have my "box" (router) provided by my ISP and then I just plug a cable in it and to my computer. 

And... nothing is happening:p! I had another computer next to me on Windows and I plugged the same cable inside the Windows one, and the connection was good (almost 922Mbit/s). So I think the problem is coming from my computer.

I've investigated a bit, here is the response from "ethtool eth0" :
```
ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: off
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x000020c6 (8390)
                   probe link rx_err tx_err hw
    Link detected: yes
```

So I should support 1000Mbit technically. I've ran "lspci" and here is my network controller:
```
05:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)


```

Here is the response of "ethtool -i eth0" :
```
ethtool -i eth0 
driver: jme
version: 1.0.8
firmware-version: 
bus-info: 0000:05:00.5
supports-statistics: no
supports-test: no
supports-eeprom-access: no
supports-register-dump: yes
supports-priv-flags: no


```

So I wasn't having any internet at all. I mean nothing was happening on the computer, it was just like nothing was plugged in it. And I checked on my router and no light was blinking like it should normally do when a cable is plugged in a Gigabit port.

So I ran the command line 
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

And then suddenly the connexion appeared and I got internet. But I was limited to 100Mbit/s (and even less apparently according to speed test). When I tried the same command to go up to 1000 at speed, the connection was lost. 

So I do not have any clue about what to do. I'm currently updating to Ubuntu 10.10 but I don't think this will resolve anything.

If anyone has any ideas, I'll be very glad to here them.

---

### Post by TheFu on 2014-12-16
Is the cable CAT5e or better? Check that first.
Try a different GigE port on the switch/router - I would swap the ports between the Windows and Linux machine, then test both again to rule out specific port issues on the router/switch.

Some NIC drivers suck and need special settings.  Google for the specific driver module settings to get YOUR card working. [http://ubuntuforums.org/showthread.php?t=2217661](http://ubuntuforums.org/showthread.php?t=2217661) has a solution.

---

### Post by maxoudela on 2014-12-17
The cable is cat5e and working fine. I've tested different port on the router but nothing is happening.

I've made some research from the link you gave me and apparently my card is the source of the problem.

I've tested this solution here : [https://thefrozenfire.com/2011/09/jmicron-jmc250-gigabit-nic-speed-issue-in-linux/](https://thefrozenfire.com/2011/09/jmicron-jmc250-gigabit-nic-speed-issue-in-linux/) but it was not working.

I saw the exact same problem here : [http://ubuntuforums.org/showthread.php?t=2102394](http://ubuntuforums.org/showthread.php?t=2102394) and it's not resolved.

I've also read this somewhere :
> According to your description, I think you may use our last generation  Gigabit Ethernet controller – JMC251A, this chip was mass production at  2008Y, at that time, the IEEE802.3az specification was not ready yet. So  the JMC251A chip might have a connection issue when it connects to  other Gigabit Ethernet controller which supports IEEE802.3az and the  ‘Speed & Duplex’ of JMC251A sets to ”Auto Negotiation” or  ”1Gbps/Full Duplex”, then the link function will abnormal. Therefore our  S/W engineer made a workaround – ASD(Auto-Speed-Down) function to force  the LAN speed keeping in 100Mbps when user sets the ‘Speed &  Duplex’ to “Auto Negotiation” or ”1Gbps/Full Duplex”. My suggestion is  to use non-support IEEE802.3az Gigabit switch then your connection speed  would keep as 1Gbps.

So the problem may be coming from that.. The thing I don't understand is that I have a Gigabit connection at work and I have no issue with Ubuntu. The connection is established at 1000Mbits/s without nothing to do. 

I've borrowed a switch in order to try to go through it but nothing happened.

I'm kind lost here. I've googled thousand times the "JMicron JMC250 ethernet problem" and I haven't find a solution. Everyone is forcing the speed to 1000 through ethtool and it seems to work but not on my side..

---

### Post by TheFu on 2014-12-17
I expect the switches where you work are old and do not support IEEE802.3az.
Seems you have 2 choices.
* Spend $25 and get an Intel PRO/1000 NIC (these are the industry standard)
* find a switch that doesn't have IEEE802.3az - and you are positive it doesn't, then follow the instructions from the links to set autonegotiation and 1000base-tx.

I can recall the days when getting **any** GigE NIC to connect at all was hard. The fact that pretty much any NIC works with any switch these days is amazing.

---

### Post by maxoudela on 2014-12-17
Thank for your reply.

I have a laptop so I can't change my NIC right?

The thing that worry me is that I don't think my switch at work are old.. I'll ask them but we have 10Gbit connection there with Cat6 RJ45 cable so..

Also note that I have a dual boot on the same computer, and on windows I'm also blocked 100Mb/s ! Even when I set autonegociation on or 1Gb it's not working. But when I'm at work, the internet is working at 1000Mb. So maybe something is on with my router.. 

You think there's nothing I can do on my computer? Maybe an updated version of the JMicron driver? Because getting a hand on a switch that does not support IEEE802.3az will not be easy...

---

### Post by TheFu on 2014-12-17
Whether you can swap the NIC on a laptop depends on how the NIC is integrated.
You can always disable the NIC in BIOS, then use a USB NIC.  There are USB3-to-GigE devices. Have use one on a chromebook - actually using it now.  $20 thru amazon. For 14.04 and later releases, "it just worked." Prior to that, I had to build a kernel module.

I'd think getting a switch for home that don't support IEEE802.3az should be easy. Just don't buy the extra, extra, energy efficient models. Check the specs. $15-$20 should do it.

JMicron is NOT a well respected vendor in networking. Feel free to look for new drivers. You might get lucky.

---

### Post by maxoudela on 2014-12-18
Thing is I don't have a USB3 port on my laptop, only USB 2... I'll try to get my hand on a switch that don't support IEEE802.3az then. A friend also told me to try to update the BIOS on my computer so I'll try to do that but I don't think this will resolve the problem..

I'll keep you posted, thanks for the help

---

### Post by TheFu on 2014-12-27
Please mark thread as solved, if solved.

---

### Post by maxoudela on 2015-01-05
Well technically the problem is not solved. I'm currently stuck to 100Mbit. But the problem seems unsolvable apart from the hacky work-around we listed in the thread. Should I mark the thread as resolved anyway?

---

### Post by TheFu on 2015-01-05
Completely a judgment call.

To me [solved] means that something has been learned - in your case, it appears to be a hardware issue since windows on the same machine doesn't do anything better.  Letting other people know that would be helpful?

---

