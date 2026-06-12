---
title: "direct cable connect ubuntu + mac with gigabit cat 6 ethernet for speed (help please)"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by jcobbers on 2007-08-18
How do I set up a direct cable connect Gigabit connection for backing up files? 

My setup is:
- ubuntu feisty fawn server (with gigabit capable eth0 port)
- mac osx macbook pro (with gigabit capable ethernet port)
- connecting the two with a brand new cat 6 patch cable

I can sustain 10 Megabits per second transfer speeds. I look in Network Preferences on the mac and it shows it is connected at 100baseTX, full duplex, flow control. On Ubuntu it's also at 100baseTx.

Why?

They support gigabit, why don't they connect automatically at that speed?

And how can I manually fix this?

Thanks! I'm new so if this is obvious I'll appreciate any help. I've spent an hour reading the forums, but haven't found anything yet. 

----
```

j@ub1:~$ sudo ethtool eth0
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
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

```

---

### Post by jcobbers on 2007-08-18
UPDATE: 

I bought a gigabit switch and a new cat 6 cable in case that was the problem. I tested direct connect and via the switch. 

I just can't get gigabit connection speeds. I'm baffled.

i've been reading these links: 
[http://lists.us.dell.com/pipermail/linux-poweredge/2005-November/023318.html](http://lists.us.dell.com/pipermail/linux-poweredge/2005-November/023318.html)
[http://www.busybuddha.org/blog/anil/entry/notes_on_gigabit_ethernet_ubuntu](http://www.busybuddha.org/blog/anil/entry/notes_on_gigabit_ethernet_ubuntu)
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/119337](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/119337) (do i need e1000-ich9 instead of e1000?)
but nothing still...

---

### Post by jcobbers on 2007-08-18
When I do the following (ubuntu is connected to a gigabit switch, with a macbook also plugged in to the switch):
```

sudo ifdown eth0
sudo ifup eth0
sudo ethtool -s eth0 speed 1000 duplex full 

```


I get this in dmesg

```

[ 8248.104144] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[ 8248.108072] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 8263.216001] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex
[ 8263.217843] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 8265.971279] e1000: eth0: e1000_watchdog: NIC Link is Down

```


Is this e1000 the gigabit driver, which is different from the 100baseT driver? 

I'm over my head here. Should I buy a new gigabit card?  All I want is faster backups, using gigabit ethernet.

---

### Post by netztier on 2007-08-18
> **jcobbers said:**
> When I do the following (ubuntu is connected to a gigabit switch, with a macbook also plugged in to the switch):
```

sudo ifdown eth0
sudo ifup eth0
sudo ethtool -s eth0 speed 1000 duplex full 

```


No need to configure duplex with Gigabit. 1000baseTX is always full duplex. The only half duplex implementation of Gigagbit I've ever seen was on a very special cisco-proprietary "GigaStack" GBIC.

Always, always, always remember: NEVER configure a duplex mode on only one end of a link. Always configure BOTH ends of the link to the same mode! If not, you risk a duplex mismatch.

> **jcobbers said:**
> 
I get this in dmesg
```

[ 8248.104144] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[ 8248.108072] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 8263.216001] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex
[ 8263.217843] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 8265.971279] e1000: eth0: e1000_watchdog: NIC Link is Down

```


This is strange - I run more than one e1000 card myself and never had any problems, even on non-PC architectures. Are you sure that the cable is Cat6 and positively has 8 wires (all four pairs) and properly twisted at that? Gigabit needs all 8 wires to run, whereas 100Mbit only needed four. 

With "classical" 100Mbit, you'd have needed a crossover cable to connect two PCs together - Gigabit doesn't need these anymore, the Auto-MDI/MDI-X feature is now standard, so it shouldn't be that, either.

What does the Mac say about the link speed when connected to the switch?

best regards

Marc

---

### Post by cmdrunix on 2007-08-22
Did you have any more luck with this anybody ??

I have a G5 connected with Cat6 to a netgear GB switch and My Ubuntu box attached to the switch with Cat6. The GB interface on Ubuntu is Yukon Gold. I actually have 2 GB interfaces both using skge on the Ubuntu box. Running iperf I am unable to get the speed above 450mbps. I have Even tried to connect them together with a GB x-over cable but the speed doesn't go over 450 or 460 mbps. I was thinking I would see somewhere around 800 or 900 mbps.

Any Ideas ?

---

### Post by netztier on 2007-08-22
> **cmdrunix said:**
> Did you have any more luck with this anybody ??

I have a G5 connected with Cat6 to a netgear GB switch and My Ubuntu box attached to the switch with Cat6. The GB interface on Ubuntu is Yukon Gold. I actually have 2 GB interfaces both using skge on the Ubuntu box. Running iperf I am unable to get the speed above 450mbps. I have Even tried to connect them together with a GB x-over cable but the speed doesn't go over 450 or 460 mbps. I was thinking I would see somewhere around 800 or 900 mbps.

Any Ideas ?

That could be normal - on my first attempts with iPerf, my numbers weren't any higher. Possible issues:

[LIST]
[*]flowcontrol state between NIC and Switch, both ends should agree. mii-tool or ethtool might deliver some information about it, as well as the switch's user interface (if available). Enable flow control if possible.
[*] use multiple parallel streams in iPerf (-P <number> parameter)
[*] increase TCP window size in iPerf (-w <value> parameter), where <value> can range from 1k to 256k
[/LIST]

best regards

Marc

---

### Post by cmdrunix on 2007-08-22
OK I played around with -P and TCP window sizes. Also tried it with a direct cable by-passing the switch and the most I can get is 680mbps. So I am guessing this must account for some ethernet and gigE hardware overhead. So I am guessing that connecting 2 machines together and only getting 680 that 680-700 is probably the most I will ever get --  Truth in Gigabit I guess :-)

---

### Post by netztier on 2007-08-22
> **cmdrunix said:**
> o I am guessing that connecting 2 machines together and only getting 680 that 680-700 is probably the most I will ever get --  Truth in Gigabit I guess :-)

Well - that's not bad at all. I have similar results between a e1000- (in a P-III 500MHz) and an skge-running card (in a 1.8Ghz Athlon64) and a (managed) Linksys Switch between them. 700Mbit/s is quite good - and most certainly up to par with what almost any application and Disk-I/O subsystems are able to deliver.

Suggestion: play also with the -t <seconds> (total time) and -i <seconds> (report results every so often) parameters, and for the comfort of it, use -r to measure first in one, then in the other direction.
And if you really want to make your systems wince under the load, use -d (simultaneous bidirectional). :-)

best regards

Marc

---

### Post by wirelessmonkey on 2007-08-22
Is this network card integrated, pci, pci-E, or pciX?
Unless the NIC has full 64 bit support over a faster bus than PCI, you can't actually get full throughput.

---

### Post by cmdrunix on 2007-08-22
The Gig card on the Mac are a Dual 1.8 G5 Desktop - on board GigE, I also have a MacBook Pro Dual Intel core2 - using on board GigE. I am trying to connect both to my Ubuntu server on an Athlon 3000, with the on board GigE -- It is an ASUS motherboeard using the skge gig driver. I also have a Belkin GigE PCI card in the Ubuntu box.

Just another update. I just connected the MAC book to the G5 directly and ran iperf and the highest I get is 450mbps. If I connect the MACBook to the Ubuntu server I get 670mbps.

I applied the Apple Braodband tuner to the G5 and still only get 450.


I am assuming that the G5 on board GigE is 64 bit since it is a Dual 1.8 G5 tower.

---

### Post by cmdrunix on 2007-08-22
Also I forgot to mention

I found another tool called ncsd [http://www-didc.lbl.gov/NCS/generic/net-tools.html](http://www-didc.lbl.gov/NCS/generic/net-tools.html)

It is even more powerful than iperf. The result when I run it on the Ubuntu box shows me  that the NIC is limited to a max throughput of 10Mb/s and when I run it is as a client on the G5 is says " the mac throughput is limited to 10Mb/s by the kernel.

What is the deal with the GigE cards setting the max Throughput to 10Mb/s. And I am sure now that there must be some setting on the G5 to get it to go above 450mbps since My MAC laptop will go up to 670 or 700.

---

