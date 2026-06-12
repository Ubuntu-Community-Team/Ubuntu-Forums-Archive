---
title: "Can't get gigabit to work in 14.04 LTS."
date: 2015-08-30
forum: Networking &amp; Wireless
---

### Post by richard.cs on 2015-08-30
I am struggling to get my onboard NIC to work at 1000BaseT on 14.04 LTS. have some memory that it worked in the dim and distant past on this machine but It's been on a 10/100 switch since before this install so it likely has never behaved on 14.04. If I run "ethtool eth0" it reports 1000 Mbps supported but not advertised, so I thought it would simply be a case of turning that on, I was wrong. When I run "sudo ethtool -s eth0 advertise 0x2f" the connection drops. If I run "ethtool eth0" again is reports that 1000baseT/Full is now advertised but the link never comes up. About 30 seconds later the link comes back (NetworkManager messing around?) but ethtool now reports the original values. Trying to force it to 1000 Mbps gives the message "Cannot advertise speed 1000". A bit of googling doesn't throw up anything with quite these symptoms, just people who have 1000BaseT advertised but not working.

I am using a cable and a switch port that I am confident are ok, they work fine on another device. Any suggestions?

Output of ethtool:
```

**richard@RCS:~$** ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
	Link detected: yes
**richard@RCS:~$** sudo ethtool -s eth0 advertise 0x2f
[sudo] password for richard:
**richard@RCS:~$** ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
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
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
	Link detected: no
**Around 30 seconds later the link comes up and...**
**richard@RCS:~$** ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
	Link detected: yes
**richard@RCS:~$** sudo ethtool -s eth0 speed 1000
Cannot advertise speed 1000


```

---

### Post by TheFu on 2015-08-31
Please post **sudo lshw -C network** output.  Appreciate the code tags. Thanks!

---

### Post by richard.cs on 2015-08-31
I only get the wrong NIC when I do that:
```
richard@RCS:~$ sudo lshw -C network
[sudo] password for richard:
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:19 memory:dfffe000-dfffffff
richard@RCS:~$
```

However if I just run lshw and trawl through the results manually I find this:
```
*-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1b:fc:e3:ce:d8
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:43 memory:dfefd000-dfefdfff ioport:d480(size=8)

```

---

### Post by TheFu on 2015-08-31
That doesn't look right for a simple setup.

Do you intend to use a virtual bridge?
Please post the complete **/etc/network/interfaces** file.

---

### Post by richard.cs on 2015-08-31
> **TheFu said:**
> That doesn't look right for a simple setup.

Do you intend to use a virtual bridge?
Please post the complete **/etc/network/interfaces** file.

I have no intention to do anything other than the simplest of setups. Not sure why the NIC is under bridges rather than network, it's not something I've ever touched.

```
richard@RCS:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

richard@RCS:~$
```

---

### Post by TheFu on 2015-08-31
Well - if you used the GUI to setup the network, then go back through that and look for any "bridge" setting - might be a checkbox.  I don't use the GUI for network stuff.

One other shot in the dark - was any virtualization hypervisor installed?

---

### Post by richard.cs on 2015-08-31
I don't think anything has been changed from the default settings except perhaps a static IP although I think I may have done that on the router this time. I think the bridge thing is a red herring, according to the lshw docs bridge is in the sense of "internal bus converter" not "network bridge". My network interface coming up under bridges is, I believe, because the MCP61 is a southbridge chip that includes a network interface. lspci gives a whole list of MCP61 devices, one of which is ethernet, see below.

```

00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 8234
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 43
        Memory at dfefd000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d480 [size=8]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] MSI: Enable+ Count=1/8 Maskable+ 64bit+
        Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
        Kernel driver in use: forcedeth

```

Apparently it is normal to have no eth0 entry in /etc/network/interfaces when NetworkManager is used. That I haven't changed but if it's likely to be part of the problem I'm happy enough to trash it and go back to manual network management. Any further thoughts on the 1000BaseT problem?


**Edit:**
Potentially related? Same chipset and driver
[http://ubuntuforums.org/showthread.php?t=1813282]("http://ubuntuforums.org/showthread.php?t=1813282")
[http://ubuntuforums.org/showthread.php?t=1345088]("http://ubuntuforums.org/showthread.php?t=1345088")

---

### Post by TheFu on 2015-08-31
The "bridge" alone isn't the issue - just really odd.  When trying to solve any issue - simplify, modify, test. Simplify, modify, test.

The reasoning for "bridge" is incorrect.  A bridge in the network world has ZERO to do with south-bridge/north-bridge chipsets.  A reasonable guess, just not right in this situation. ;)

Something on the system is asking/forcing a network bridge. This is NOT the default. I've only seen Linux bridges used when doing complicated routing or when having multiple virtual network interfaces connected to a single physical port. This is commonly used when running virtual machines or containers.  When using those, network manager gets in the way and it is best to purge it from the box.  Based on what you've said, you aren't doing either of those things, so the bridge is just odd.

[https://askubuntu.com/questions/611781/ethernet-connection-not-working-after-installing-ubuntu-14-04-lts](https://askubuntu.com/questions/611781/ethernet-connection-not-working-after-installing-ubuntu-14-04-lts) 
Looks like the wrong driver options might be used. [https://bbs.archlinux.org/viewtopic.php?pid=1551149#p1551149](https://bbs.archlinux.org/viewtopic.php?pid=1551149#p1551149) But those folks didn't have any network connection at all.  Still - seems related.

If you want to fight with this chip, great. There are a few more things to try.
If you just want working GigE networking - get an Intel PRO/1000 card for $30. It uses the e1000 driver - industry standard.

---

### Post by richard.cs on 2015-08-31
So you're fairly sure that coming up as bridge under lshw means it is configured as a network bridge not just a quirk of the chipset? That would certainly be very odd and I am absolutely certain that's not something I've ever done, hence why I thought it could only refer to the other kind.

I'm happy to fight with this one, but there are spare PCI slots if I have to admit defeat. What would you suggest next?

---

### Post by TheFu on 2015-08-31
So - your response got me looking ... at the whole "bridge" thing from lshw.  That is showing how things are connected inside the system and you are correct that it isn't related to "network bridging" at all. The top part of my post #8 above is incorrect and not useful.  "Red herring" as you say is true.

If there isn't output from **lshw -C network**, then the device shouldn't work at all - it isn't recognized by the OS/drivers as a network device. I'm surprised **any** packets flow at all.

Did you try those driver options in the post #8 links?

So - ***when the wired network*** is working, please post the output of these commands:
* sudo lshw -C network
* route
* ifconfig
Include wireless and wired connections, if shown, please. That will provide a complete picture of the networking. I don't want the wifi network enabled when these commands are run, if that has been setup.

---

### Post by richard.cs on 2015-08-31
I haven't tried the driver options suggested in post 8 yet, I'm not actually at home and didn't want to go poking too hard over ssh. I will try them next time I get a chance, either later tonight or tomorrow.

With wired networking working, wireless never setup and not used:
```
richard@RCS:~$ sudo lshw -C network
[sudo] password for richard:
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:19 memory:dfffe000-dfffffff
richard@RCS:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
richard@RCS:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:e3:ce:d8
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fee3:ced8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12063749 errors:30 dropped:0 overruns:28 frame:2
          TX packets:128478917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1300901391 (1.3 GB)  TX bytes:193727123066 (193.7 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:45032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4305597 (4.3 MB)  TX bytes:4305597 (4.3 MB)

richard@RCS:~$

```

I am certain that the BCM4318 is not currently in use, also note that the MAC address of eth0 appears to match the serial number of the -bridge device (in the earlier posts).

---

### Post by TheFu on 2015-08-31
Thank you! Didn't think wifi was related, but had to ask to be certain.  I'll see what I can find in the next hour to explain the missing -C network section ... 

[https://askubuntu.com/questions/78256/lspci-and-lshw-show-no-network-devices](https://askubuntu.com/questions/78256/lspci-and-lshw-show-no-network-devices) - related?

In the ifconfig output above - see the 30 errors? Check the cable and try a different port on the switch/router. Shouldn't be any errors.

A few of my systems:
```
eth0      Link encap:Ethernet  HWaddr 80:ee:73:07:bb:b6  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173045637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33463949 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:224059446680 (224.0 GB)  TX bytes:157534313266 (157.5 GB)
          Interrupt:17
```
Zero errors in 157G transfered. That is a bridge, hence no IP assigned to the eth0 device.
 
Definitely check the port and cable - a less-than-perfect connect CAN prevent GigE speeds. For the driver stuff - please review the links.

---

### Post by richard.cs on 2015-08-31
It could be related but again, for that person networking didn't work at all. Showing up in the wrong class but working doesn't seem quite the same.

I've tried two cables and two ports (in all the 4 combinations). All worked with my gigabit NAS and none worked with the PC. Oddly the link seemed to take longer to come up on the PC, the NAS comes up almost instantly, the gigabit light on the switch turns on and stays on. With the PC the gigabit light blinks for a second or two before going out. I'd agree that might signify physical layer problems but the cables and switch ports do work with another device. I guess it's possible I have a physically damaged network interface but I think it's unlikely.

I'll try some other cables and ports when I get a chance, it's possible that the PC is less tolerant of a marginal PHY layer. Is it possible those errors relate to my swapping cables and general messing around while data was being transferred?

---

### Post by TheFu on 2015-08-31
If you were pulling and inserting cables while traffic was being attempted, that could easily cause errors.

Since you've already swapped the ports and cables, seems like those are NOT the issue. We are back to the onboard networking as the issue. If you don't see any more errors, we are back to the driver options.

Think we've exhausted my knowledge. Sorry.

---

