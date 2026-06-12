---
title: "Network interface card"
date: 2016-10-21
forum: Networking &amp; Wireless
---

### Post by RobGoss on 2016-10-21
Hello everyone I have a question and was hoping you could shed some light on it

I upgraded my network to **200 mbps** I was having some issues with some of my machines being able to reach that **200 mbps download,** upload was always consistent around **17.45**, so the bright house tech support says

The machine I'm having issues with is a Dell desktop, after doing a speed test it would only reach about 120 to 130 mbps. I had 2 techs come out to the house that couldn't tell me what was wrong

Bottom line is I was told that particular machine network interface card had a maximum of **100 mbps** output 

My question is how would I confirm this, I'm only using Linux is there anyway for me to see if this is correct using the command line?

They told me that machine can only reach **100 mbps **or less because that was the maximum but this machine is reaching around **120 to 130, **so that leads me to believe someone is not telling me the correct information

I know it might be better to just look up the make and model to find out what the specs are for that NIC

Thanks so much

---

### Post by QLee on 2016-10-21
> **RobGoss said:**
> 
I know it might be better to just look up the make and model to find out what the specs are for that NIC
A couple of things Rob.

200mb is an amount not a speed. However, we probably understand you actually mean a unit/second.  I'm going to guess a 25MB/sec service

You spend a lot of time here so you know what is likely to be asked. Specs.
You already answered your own question about that

However, maybe this is more like what want to do. You are familiar with the printouts from the Wireless Script like when it shows lshw -c net. It shows the capabilities of both wireless and wired NICs

If it wireless, then many factors can affect the throughput. Distance, what the walls in between are made of, even the orientation of the antennas. If the tech you had out isn't very experienced they may not have dealt with things like that.

A caveat, It is rare to obtain full throughput on any kind of sustained basis from any ISP in my country, that's why Internet speeds are usually listed as "up to", I can't say about your ISP.

Edit:  Ah, I see from your edit you did want a command, I hope the one I mentioned was helpful.

---

### Post by TheFu on 2016-10-21
Wired NICs are usually 100 Mbps or 1000 Mbps. I've never heard of a 200 Mbps device.
Also, don't mix up Mbps (megabits per sec) and MBps (megabytes per sec) - they are different by 8x.

100 Mbps = 100/8 = 12.5 MBps

Plus different protocols have different overhead amounts.  Usually around 5-20%. And there are switching and routing latencies all along the path.  If you are trying to measure using an internet source for data, then the slowest section of the path will be the limiting factor - that is usually the ISP.  If the PC only supports 100Mbps and the ISP is allowing 200Mbps downloads, then you'll never get faster than 100Mbps.  Cheap, cheap, 1000 Mbps adapters can top out around 260Mbps (nowhere near the 1000 Mbps spec).

As for wifi - forgetaboutit.  Wifi specs are lies, lies, lies and more lies.  wifi has so many outside issues that cannot be controlled as to make tuning it next to impossible.  Plus Dell has a habit of putting the least of the std into their equipment.  I have a 6 yr old Dell 1558 laptop that claims wifi-N capability, but it only supports 75Mbps as the best possible throughput. Best I've ever actually seen is half that (about 35Mbps) from 12 inches away.  It has a wired GigE port too and routinely gets 850-920Mbps on it over short **and** long CAT5e runs.  Wired ethernet is always better than any other method used in a house/small biz.  Fibre is even better, but I don't want to throw $3K at this issue and suspect you don't either.

Same for powerline networking, just with even more lies added.  My 600 Mbps powerline (certified) only gets 220Mbps in the same room and more like 40Mbps on different floors.  Lies, lies, lies. At least with wired ethernet, we get closer speeds, provided everything is up-to spec.  Not all ethernet cables can be used for just any connection. There are different standards for cables - CAT3, CAT5, CAT5e, CAT6, CAT6A, etc ... CAT5e should be the min deployed these days and easily handled GigE speeds over a house, even a large house.

BTW, for a wired ethernet LAN, the price for 1000 Mbps (GigE) is about the same as for 100 Mbps equipment these days, so it really doesn't make sense to bother with the slower stuff and hasn't for the last decade.  A quality GigE NIC is $25 (Intel PRO/1000). A good enough GigE 8-port switch (tp-link/dlink/whatever) is $20.  With these two things, you can transfer files around at 650-920 Mbps inside your LAN without changing the router out. That is at least 6x faster than 100 Mbps and that is without trying very hard.  Other companies sell cheaper GigE NICs too, but all of them require more CPU (20-30%) and the Intel PRO/1000 versions (1-3%) which do most of the processing in the ASIC on the card.  Is saving $10 on a NIC worth it?  Sometimes it is, but not always.

I've found cable internet techs to usually know little about IP/ethernet. They know their coax and dB loss stuff, but not so much about normal networking. Throw in Linux and they just step aside and wait for me to fix it.  That isn't to say there aren't exceptions and that some of those techs really do know their stuff, I've just never had one come to my house. OTOH, my WAN and LAN networking isn't the normal stuff seen in a small biz - lots of routers, lots of subnets and multiple WAN IPs here.

As for commands to get the info:
**sudo lshw -C network** is what I use.  I like this because it provides both HW information AND which driver is loaded and being used. You can also use **ifconfig** to see the connection speed, though it does lie sometimes.

Make a list of all the parts on the network and their theoretical throughput. PC NIC, cable, switch port, router port, WAN connection .... are they all GigE?  A GigE NIC doesn't help if there are only 100 Mbps switch/router ports. Cables need to be CAT5e at a min and that will support multi-gigabit speeds (soon). CAT5e cables are cheap. CAT6 is better, but doesn't seem to be needed, even for 10G speeds over very short distances. Anything less is a waste of your time/money. Also, if the WAN link is 200 Mbps down and 3Mbps up, then the system will never get more than that and usually about 10% less if everything is working perfectly and it is the slowest.  Speedtest.net should show something close to the 200 Mbps, if that is what you are paying for in a cable ISP connection. If it doesn't and all your stuff is GigE ( and you can transfer at GigE speeds inside the LAN ), then I'd have Brighthouse out again and show them your iperf stats.  iperf really shows the max possible, not real-world transfer rates.  I routinely see 920Mbps iperf results on my GigE network, but transfering files is usually closer to 650-700Mbps thanks to the encryption layers used (rsync + ssh).

If wifi is used, a good guess for performance is 50% less for every device added and that is under ideal situations.  So, if the wifi card in the device claims 200 Mbps (which would be strange, usually 300/150/75 Mbps are common for N-Wifi devices), then adding 1 wifi would half that to 100Mbps. Add another and that would drop each to 50Mbps - a 3rd device --> 25Mbps for each.  See how that works?  Wifi-AC does some tricks to make it a little better, but when planning, it is best to be conservative and use 50% less and less and less for each added device. Again, this is under ideal circumstances. No walls. Short distances. Line of sight. No other interference from microwaves, bluetooth, cordless phones, other wifi networks. All of those things impact throughput.  In dense wifi areas, the interference can drop throughput to only 10% (or less) of the box value - then every added device takes 50% away from that starting point. I've designed thousands of wifi deployments - and avoid it whenever possible.  

So - wifi or wired? That's the first question.

---

### Post by Hadaka on 2016-10-21
Hi to view your ethernet card open a terminal ctrl/alt/t and do..
```
lspci -nnk | grep -iA2 net
```
This will show the ethernet card and the wifi card.
Here is an older Dell computer example..
```
:~$ lspci -nnk | grep -iA2 net
02:00.0 [COLOR=#ff0000]Ethernet[/COLOR] controller [0200]: Broadcom Corporation BCM4401-B0 [COLOR=#ff0000]100[/COLOR]Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: b44
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel driver in use: b43-pci-bridge

```
The 100 base indicates a 10/100 lan card...hence the reason your isp stated he doubted you could go over 100 Mbps
The 200Mbps is probably referring to full duplex mode..you only run 1/2 duplex. Read the link below for a better understanding.
[https://www.safaribooksonline.com/library/view/ethernet-the-definitive/1565926609/ch04.html](https://www.safaribooksonline.com/library/view/ethernet-the-definitive/1565926609/ch04.html)
Hope this helps.

---

### Post by SeijiSensei on 2016-10-21
You probably need to install a "gigabit" Ethernet card.  If you have a network switch involved, that needs to run at gigabit speeds as well.  

The most reliable choice is almost always Intel: [http://www.newegg.com/Product/Product.aspx?Item=9SIA24G1XA5134](http://www.newegg.com/Product/Product.aspx?Item=9SIA24G1XA5134)

---

### Post by chili555 on 2016-10-21
I suggest that you find out the interface name for your ethernet card from:```
ifconfig
```Then do:```
sudo ethtool enp-whatever-you found.
```Here is a sample from my machine:```
[COLOR="#FF0000"]enp0s25[/COLOR]: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 68:f7:28:ae:83:47  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf0600000-f0620000
``````
Settings for [COLOR="#FF0000"]enp0s25[/COLOR]:
	Supported ports: [ TP ]
	[COLOR="#FF0000"]Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full [/COLOR]
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 2
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown (auto)
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: no

```In my example, my card will support 1000 Mbps. It currently shows Speed: Unknown because it isn't connected.

---

### Post by RobGoss on 2016-10-21
> **Hadaka said:**
> Hi to view your ethernet card open a terminal ctrl/alt/t and do..
```
lspci -nnk | grep -iA2 net
```
This will show the ethernet card and the wifi card.
Here is an older Dell computer example..
```
:~$ lspci -nnk | grep -iA2 net
02:00.0 [COLOR=#ff0000]Ethernet[/COLOR] controller [0200]: Broadcom Corporation BCM4401-B0 [COLOR=#ff0000]100[/COLOR]Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: b44
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel driver in use: b43-pci-bridge

```
The 100 base indicates a 10/100 lan card...hence the reason your isp stated he doubted you could go over 100 Mbps
The 200Mbps is probably referring to full duplex mode..you only run 1/2 duplex. Read the link below for a better understanding.
[https://www.safaribooksonline.com/library/view/ethernet-the-definitive/1565926609/ch04.html](https://www.safaribooksonline.com/library/view/ethernet-the-definitive/1565926609/ch04.html)
Hope this helps.



From the following:
```
lspci -nnk | grep -iA2 net
```

```
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)	Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter [1028:020c]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:068d]
	Kernel driver in use: r8169
	Kernel modules: r8169
robert@robert-Inspiron-3646:~$ clear
robert@robert-Inspiron-3646:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter [1028:020c]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:068d]
	Kernel driver in use: r8169
	Kernel modules: r8169

```



I did not see anything like 100-base so I'm not sure what I'm looking at

---

### Post by RobGoss on 2016-10-21
> **chili555 said:**
> I suggest that you find out the interface name for your ethernet card from:```
ifconfig
```Then do:```
sudo ethtool enp-whatever-you found.
```Here is a sample from my machine:```
[COLOR=#FF0000]enp0s25[/COLOR]: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 68:f7:28:ae:83:47  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf0600000-f0620000
``````
Settings for [COLOR=#FF0000]enp0s25[/COLOR]:
    Supported ports: [ TP ]
    [COLOR=#FF0000]Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full [/COLOR]
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: Unknown!
    Duplex: Unknown! (255)
    Port: Twisted Pair
    PHYAD: 2
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown (auto)
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: no

```In my example, my card will support 1000 Mbps. It currently shows Speed: Unknown because it isn't connected.


Hello Chili555 I'm not really sure how to run that command you suggested thanks :)

---

### Post by RobGoss on 2016-10-21
> **SeijiSensei said:**
> You probably need to install a "gigabit" Ethernet card.  If you have a network switch involved, that needs to run at gigabit speeds as well.  

The most reliable choice is almost always Intel: [http://www.newegg.com/Product/Product.aspx?Item=9SIA24G1XA5134](http://www.newegg.com/Product/Product.aspx?Item=9SIA24G1XA5134)


Yes Sir I was thinking about bumping my card a little if needed thanks so much

---

### Post by RobGoss on 2016-10-21
> **QLee said:**
> A couple of things Rob.

200mb is an amount not a speed. However, we probably understand you actually mean a unit/second.  I'm going to guess a 25MB/sec service

You spend a lot of time here so you know what is likely to be asked. Specs.
You already answered your own question about that

However, maybe this is more like what want to do. You are familiar with the printouts from the Wireless Script like when it shows lshw -c net. It shows the capabilities of both wireless and wired NICs

If it wireless, then many factors can affect the throughput. Distance, what the walls in between are made of, even the orientation of the antennas. If the tech you had out isn't very experienced they may not have dealt with things like that.

A caveat, It is rare to obtain full throughput on any kind of sustained basis from any ISP in my country, that's why Internet speeds are usually listed as "up to", I can't say about your ISP.

Edit:  Ah, I see from your edit you did want a command, I hope the one I mentioned was helpful.

Thanks so much for the help, I'm using all **Ethernet connections** for at least **three** of my machines I understand **WiFi **connections may differ depending on how strong your signal is. I just wanted to make sure I have what I'm paying for if you know what I mean

---

### Post by RobGoss on 2016-10-21
> **SeijiSensei said:**
> You probably need to install a "gigabit" Ethernet card.  If you have a network switch involved, that needs to run at gigabit speeds as well.  

The most reliable choice is almost always Intel: [http://www.newegg.com/Product/Product.aspx?Item=9SIA24G1XA5134](http://www.newegg.com/Product/Product.aspx?Item=9SIA24G1XA5134)

Yes I was thinking about bumping up my card also I will take a look at the link you posted, thanks so much

---

### Post by chili555 on 2016-10-21
> **RobGoss said:**
> Hello Chili555 I'm not really how to run that command you suggested thanks :)Open a terminal with Ctrl+Alt+t. Type in:```
ifconfig
```Press Enter. You will find your ethernet interface designation, enp-something or eth-something. Use the information for the next command:```
sudo ethtool eth0
```Or whatever your interface is, if not eth0. Press Enter. 

Post the results here.

---

### Post by RobGoss on 2016-10-21
> **TheFu said:**
> Wired NICs are usually 100 Mbps or 1000 Mbps. I've never heard of a 200 Mbps device.
Also, don't mix up Mbps (megabits per sec) and MBps (megabytes per sec) - they are different by 8x.

100 Mbps = 100/8 = 12.5 MBps

Plus different protocols have different overhead amounts.  Usually around 5-20%. And there are switching and routing latencies all along the path.  If you are trying to measure using an internet source for data, then the slowest section of the path will be the limiting factor - that is usually the ISP.  If the PC only supports 100Mbps and the ISP is allowing 200Mbps downloads, then you'll never get faster than 100Mbps.  Cheap, cheap, 1000 Mbps adapters can top out around 260Mbps (nowhere near the 1000 Mbps spec).

As for wifi - forgetaboutit.  Wifi specs are lies, lies, lies and more lies.  wifi has so many outside issues that cannot be controlled as to make tuning it next to impossible.  Plus Dell has a habit of putting the least of the std into their equipment.  I have a 6 yr old Dell 1558 laptop that claims wifi-N capability, but it only supports 75Mbps as the best possible throughput. Best I've ever actually seen is half that (about 35Mbps) from 12 inches away.  It has a wired GigE port too and routinely gets 850-920Mbps on it over short **and** long CAT5e runs.  Wired ethernet is always better than any other method used in a house/small biz.  Fibre is even better, but I don't want to throw $3K at this issue and suspect you don't either.

Same for powerline networking, just with even more lies added.  My 600 Mbps powerline (certified) only gets 220Mbps in the same room and more like 40Mbps on different floors.  Lies, lies, lies. At least with wired ethernet, we get closer speeds, provided everything is up-to spec.  Not all ethernet cables can be used for just any connection. There are different standards for cables - CAT3, CAT5, CAT5e, CAT6, CAT6A, etc ... CAT5e should be the min deployed these days and easily handled GigE speeds over a house, even a large house.

BTW, for a wired ethernet LAN, the price for 1000 Mbps (GigE) is about the same as for 100 Mbps equipment these days, so it really doesn't make sense to bother with the slower stuff and hasn't for the last decade.  A quality GigE NIC is $25 (Intel PRO/1000). A good enough GigE 8-port switch (tp-link/dlink/whatever) is $20.  With these two things, you can transfer files around at 650-920 Mbps inside your LAN without changing the router out. That is at least 6x faster than 100 Mbps and that is without trying very hard.  Other companies sell cheaper GigE NICs too, but all of them require more CPU (20-30%) and the Intel PRO/1000 versions (1-3%) which do most of the processing in the ASIC on the card.  Is saving $10 on a NIC worth it?  Sometimes it is, but not always.

I've found cable internet techs to usually know little about IP/ethernet. They know their coax and dB loss stuff, but not so much about normal networking. Throw in Linux and they just step aside and wait for me to fix it.  That isn't to say there aren't exceptions and that some of those techs really do know their stuff, I've just never had one come to my house. OTOH, my WAN and LAN networking isn't the normal stuff seen in a small biz - lots of routers, lots of subnets and multiple WAN IPs here.

As for commands to get the info:
**sudo lshw -C network** is what I use.  I like this because it provides both HW information AND which driver is loaded and being used. You can also use **ifconfig** to see the connection speed, though it does lie sometimes.

Make a list of all the parts on the network and their theoretical throughput. PC NIC, cable, switch port, router port, WAN connection .... are they all GigE?  A GigE NIC doesn't help if there are only 100 Mbps switch/router ports. Cables need to be CAT5e at a min and that will support multi-gigabit speeds (soon). CAT5e cables are cheap. CAT6 is better, but doesn't seem to be needed, even for 10G speeds over very short distances. Anything less is a waste of your time/money. Also, if the WAN link is 200 Mbps down and 3Mbps up, then the system will never get more than that and usually about 10% less if everything is working perfectly and it is the slowest.  Speedtest.net should show something close to the 200 Mbps, if that is what you are paying for in a cable ISP connection. If it doesn't and all your stuff is GigE ( and you can transfer at GigE speeds inside the LAN ), then I'd have Brighthouse out again and show them your iperf stats.  iperf really shows the max possible, not real-world transfer rates.  I routinely see 920Mbps iperf results on my GigE network, but transfering files is usually closer to 650-700Mbps thanks to the encryption layers used (rsync + ssh).

If wifi is used, a good guess for performance is 50% less for every device added and that is under ideal situations.  So, if the wifi card in the device claims 200 Mbps (which would be strange, usually 300/150/75 Mbps are common for N-Wifi devices), then adding 1 wifi would half that to 100Mbps. Add another and that would drop each to 50Mbps - a 3rd device --> 25Mbps for each.  See how that works?  Wifi-AC does some tricks to make it a little better, but when planning, it is best to be conservative and use 50% less and less and less for each added device. Again, this is under ideal circumstances. No walls. Short distances. Line of sight. No other interference from microwaves, bluetooth, cordless phones, other wifi networks. All of those things impact throughput.  In dense wifi areas, the interference can drop throughput to only 10% (or less) of the box value - then every added device takes 50% away from that starting point. I've designed thousands of wifi deployments - and avoid it whenever possible.  

So - wifi or wired? That's the first question.

I'm using a wired connection on the machines in question I know WiFi may differ depending on how strong your signal is I might tackle that later down the road

I'm trying to see what my card supports as far as MBPS I think I said that correctly This machine is not that old maybe about three years old It's a **Dell Inspiron** 3646, **4-GB** Ram, **500-GB** hard drive,   **Intel Celeron J1800 / 2.41 GHz**

 I ran this to see my graphic card

```
lspci | grep VGA
```
```
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]

```

---

### Post by chili555 on 2016-10-21
Here is a sample of the ethtool command I suggested above run from my machine while connected.```
Settings for enp0s25:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	[COLOR="#FF0000"]Speed: 1000Mb/s[/COLOR]
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

### Post by RobGoss on 2016-10-21
Here's what I get for that command:
```
 Settings for enp3s0:	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	                                     1000baseT/Full 
	Link partner advertised pause frame use: Symmetric
	Link partner advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

```

---

### Post by chili555 on 2016-10-21
> Speed: 1000Mb/sYours is a gigabit or 1000 Mbps card. What is the speed advertised for the service you are buying from your internet service provider? Next, what speed are you actually getting from here? [http://beta.speedtest.net/](http://beta.speedtest.net/) 

Please be aware that there is some overhead involved here. If an ISP says they are providing, say 100 Mbps service, a real life test won't be exactly 100 Mbps, it will be a bit less.

[http://stackoverflow.com/questions/3613989/what-of-traffic-is-network-overhead-on-top-of-http-s-requests](http://stackoverflow.com/questions/3613989/what-of-traffic-is-network-overhead-on-top-of-http-s-requests)

I am buying gigabit service, however, my most recent speed test yielded 928.33 Mbps speeds which I consider excellent.

---

### Post by RobGoss on 2016-10-21
> Yours is a gigabit or 1000 Mbps card. What is the speed advertised for the service you are buying from your internet service provider? Next, what speed are you actually getting from here? [http://beta.speedtest.net/](http://beta.speedtest.net/)

First try using the tool you provided I got the following, Download - **171.95**, Upload, - [B]17.43

[/B]Second try I got the following, Download - **186.71**,, Upload, - [B]17.31

[/B]The upload is always consistent and always on track. I been using the speed test tool from my provider Bright House, here's the link for that site maybe it's not the greatest tool for checking the speed, [speedtest.bhn.net ]("http://speedtest.bhn.net")

So after seeing my specs for the network interface card would you say I'm suppose to getting more them 100 mbps? this is my assumption

This is my provider I'm got the **Lightning 200 ** [https://brighthouse.com/shop/internet.html](https://brighthouse.com/shop/internet.html)

Thanks so much for taking the time to help answer this for me much appreciated

---

### Post by chili555 on 2016-10-21
I'd say that if you are buying the Lightning 200, you are right on track! 200 Mbps minus some overhead is very consistent with your speed test results. 

Breathe easy.

---

### Post by RobGoss on 2016-10-21
So my network interface card is not **100** as my provide stated and only able to receive 100 mbps and under correct? 

Breathing easy here \\:D/

---

### Post by chili555 on 2016-10-21
Your network card is a 1000 Mbps card. It will negotiate with a router, switch or other access point down to 100 or 10 Mbps and receive and send anything in that range. Everything you've shown us so far suggests that your card and internet service provider are working perfectly well.

---

### Post by TheFu on 2016-10-21
If I assume that you have GigE networking on the LAN and have 200Mbps/20Mbps ISP service, then everything seems to be working pretty well.  The techs assumed you have 100Mbps network cards, since most people will only have that, not GigE cards. Theirs is a reasonable assumption without the ability to check it. Running Linux probably means they don't have the knowledge to check it.

Also recognize that most websites won't push that speed.  They will cap your data xfer to some much lower value. For example, GA-Tech limits downloads to 1.5Mbps for people who aren't on campus.  Having a huge WAN pipe is most helpful if you are using multiple multiple services concurrently.  BTW, I'm jealous of your bandwidth.  Maybe in 2 more yrs, I'll be able to get fast, relatively cheap, GigE service.  Lots of fibre is being put in the ground nearby.  Comcast wants $300/month for 250/25Mbps service here without static IPs.

Please be very careful with capitalization.  Mbps != MBps  and "MBPS" is ambiguous. Clarity and accuracy is important.

---

### Post by chili555 on 2016-10-21
> Lots of fibre is being put in the ground nearby. Comcast wants $300/month for 250/25Mbps service here without static IPs.
AT&T gets $70 for 1000 Mbps here; it is assumed the price is set to compete with Google fiber. I have it and, so far, it's great!

---

### Post by RobGoss on 2016-10-22
> The techs assumed you have 100Mbps network[COLOR=#000000] [/COLOR]

Yes and he told me this over the phone just by looking at I guess there networking system they have over there


> BTW, I'm jealous of your bandwidth. Maybe in 2 more yrs, I'll be able to get fast, relatively cheap, GigE service. Lots of fibre is being put in the ground nearby. Comcast wants $300/month for 250/25Mbps service here without static IPs.


How can you tell what my bandwidth is and what should I be looking for just wondering

Thanks so much

---

### Post by chili555 on 2016-10-22
> How can you tell what my bandwidth is and what should I be looking for just wondering
You said you were paying for Lightning 200. Your speed tests seem to confirm that you are getting exactly that.

Breathe easy and enjoy it!

---

### Post by RobGoss on 2016-10-22
Just wanted to make sure I knew what I was looking at Thanks so much for the help I will mark this as solved

---

### Post by TheFu on 2016-10-22
> **chili555 said:**
> You said you were paying for Lightning 200. Your speed tests seem to confirm that you are getting exactly that.

Breathe easy and enjoy it!

Exactly. speedtest.

The bandwidth shown on speedtest is what I would have expected for a 200Mbps connection.  There is usually about 10-15% overhead in the network, so 200 x .88 = 176 ... which is what you are seeing.  Anything higher than that is gravy.

---

### Post by RobGoss on 2016-10-22
Thanks so much TheFu much appreciated for all your help and time

---

