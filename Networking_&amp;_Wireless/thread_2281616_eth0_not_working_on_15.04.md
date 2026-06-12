---
title: "eth0 not working on 15.04"
date: 2015-06-08
forum: Networking &amp; Wireless
---

### Post by BeachBuddah on 2015-06-08
Hello all from NY,

I have a recent clean install of 15.04 and have encountered no problems at all as I personalized it over the last few days...until I tried connecting via a cable to the net.  My wlan0 worked out of the box with no worries, but I am a bit lost now.  I have an hp DV6 Envy laptop with a Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller.  When I check System Settings > Network all I see is 'Cable Unplugged'.  Looking at the drop down menu for Network Manager, the first listings 'Ethernet Network' and 'Disconnected' are greyed out, though the cable is plugged in (and that cable is the second cable I've tried and in three different network ports, so those aren't the culprits).

To be sure I am only getting eth0 output, I turned off wlan0 and ran ifconfig with the following output:
```
root@cristo:~# ifconfig
eth0      Link encap:Ethernet  HWaddr a0:b3:cc:50:65:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:614306 (614.3 KB)  TX bytes:614306 (614.3 KB)

```

This is output for ip link:

```
root@cristo:~# ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether a0:b3:cc:50:65:14 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN mode DEFAULT group default qlen 1000
    link/ether 1c:3e:84:29:cb:53 brd ff:ff:ff:ff:ff:ff

```

And here is netstat -i

```
root@cristo:~# netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BMU
lo        65536 0      9797      0      0 0          9797      0      0      0 LRU[CODE]

And ethtool:
[CODE]
root@cristo:~# ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no
```

Lots of data - which I admit acquiring by praying to the google for answers before coming here but only getting the above suggestions and no fixes.

TIA for all your help in this issue.  If any further output is needed, please ask - I am at the laptop all day.

Cheers!

Chris

---

### Post by TheFu on 2015-06-08
Output from **sudo lshw -C network** please.  Just to complete the picture.
Also, which version of Ubuntu GUI are you using?  Unity or something else?  What are the network settings in the GUI?

---

### Post by BeachBuddah on 2015-06-09
```
cristo@cristo:~$ sudo lshw -C network
[sudo] password for cristo: 
  *-network               
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: wlan0
       version: 00
       serial: 1c:3e:84:29:cb:53
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.19.0-20-generic firmware=0.37 ip=10.14.64.62 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:d3510000-d351ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 07
       serial: a0:b3:cc:50:65:14
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:28 ioport:2000(size=256) memory:d3404000-d3404fff memory:d3400000-d3403fff

```

As requested.  I am using Unity, but am unsure of the request: 'Network settings in GUI', unless you mean the Network Manager IPv4 settings - which are set to 'Automatic (DHCP)'.  If you meant something else, my apologies - let me know and I will provide.  Thanks for your response.

---

### Post by TheFu on 2015-06-09
So - I don't use Unity or the GUI to manage my network settings. It appears you have everything working, except the DHCP server just isn't providing the network information over the wired connection.

That means the issue is with:
* bad cable.
* bad switch port
* bad NIC port
* bad drivers (hard to say at this point, we'll assume everything is fine there for now)
* Conflicting wifi and wired settings - disable the wifi adapter completely using the GUI
* DHCP server is "full" - login to the router and make certain all the DHCP "slots" for IPs haven't been used already. 
* a few other highly unlikely things like routing, DNS, stuff like that.

So - verify that the cable isn't bad somehow, use a different switch port and/or a different wired computer to verify the cable and switch port are working for other devices.

If that doesn't fix it, please post the output from "route" and ifconfig after rebooting the router and forcing the wired PC to connect using the GUI. Do not allow the wifi to connect when you are working through these things.

---

