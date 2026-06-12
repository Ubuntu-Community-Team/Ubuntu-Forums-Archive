---
title: "Feels like dialup"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by Snipersnest on 2007-08-05
I'm trying to install Steam on Wine or Cedega but I get the same results. 

My network speed/internet is running like 56k modem speeds. Yes, I've check the Steam network setting - its on Cable/Fiber 10M .. Thats not the problem. Steam only downloads games at about 7-8kbps

Firefox seems to pull things up fine. But other downloads are very slow.

My laptop is running Gusty Gibbon and it burned up the same download on wireless in seconds. 

I'm running Feisty Fawn on my desktop with 2.6.20-16.

Motherboard: Asus A8N-SLI Premium
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)

Any ideas come to mind?

---

### Post by noob12 on 2007-08-05
What's your actual link rate?

```

sudo ethtool eth0

```

---

### Post by Snipersnest on 2007-08-05
> **noob12 said:**
> What's your actual link rate?

```

sudo ethtool eth0

```
Settings for eth1:
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
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x00000037 (55)
        Link detected: yes

Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: Unknown! (65535)
        Duplex: Unknown! (255)
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: no



I don't know much about this...so tell me whats going on.
 Just a heads up eth0 doesn't have a cable attached.

Also these were in my /var/log/syslog - Should I be concerned?
Aug  5 01:15:00 nate-desktop gconfd (nate-8519): starting (version 2.18.0.1), pid 8519 user 'nate'
Aug  5 01:15:00 nate-desktop gconfd (nate-8519): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  5 01:15:00 nate-desktop gconfd (nate-8519): Resolved address "xml:readwrite:/home/nate/.gconf" to a writable configuration source at position 1
Aug  5 01:15:00 nate-desktop gconfd (nate-8519): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  5 01:15:00 nate-desktop gconfd (nate-8519): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  5 01:15:00 nate-desktop gconfd (nate-8519): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  5 01:15:01 nate-desktop gconfd (nate-8519): Resolved address "xml:readwrite:/home/nate/.gconf" to a writable configuration source at position 0
Aug  5 01:15:01 nate-desktop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Aug  5 01:15:01 nate-desktop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

---

### Post by noob12 on 2007-08-05
This was telling us the negotiated link rate.  We were making sure that there hadn't been some autonegotiation issue.  Looks fine.  The card has negotiated a 100mbps full duplex link as expected if you're connected to a 100mbps full duplex switch.

Can you show us **ifconfig -a**?

You say that firefox is fine but other downloads are slow.  What other linux-native apps are behaving slowly?

---

### Post by Snipersnest on 2007-08-05
Well to be honest I only check my email with evolution and use firefox for surfing.  Then I use Cedega or Wine for everything else. Updates via Update Manager and Synaptic download at over 1800kbps.

I have a 15meg cable connection. So far only Wine/Cedega has dialup speed.

eth0      Link encap:Ethernet  HWaddr 00:13:D4:30:C1:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:13:D4:30:CC:DA  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe30:ccda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4718 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6728362 (6.4 MiB)  TX bytes:534493 (521.9 KiB)
          Interrupt:3 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2422 (2.3 KiB)  TX bytes:2422 (2.3 KiB)

---

### Post by noob12 on 2007-08-05
OK.  I am not sure this is a network problem.  It sounds more like a Wine/Cedega problem, which is to say only that you might find better help in a forum that is specifically about Wine or Cedega.   And which is to say I don't have any ideas. 

If you have another host in your own local network you can do more tests of bandwidth between them in order to be more confident that this isn't a general linux-level network issue.  As a relatively quick gauge, I'd use ftp of some large files or, between two linux hosts use iperf.

---

### Post by Snipersnest on 2007-08-05
I'm still trying to figure out why its so much different between two computers doing the **exact** same install. I didn't change anything or do anything special. Just my laptop is fast on Wine/Cedega and my desktop runs at 56k dialup. 

Yeah well its not a Linux issue really.. cause I can transfer files back and forth in seconds (500+ meg).  Ok I guess I'll move this to the wine forum.

Thank you for the help.

---

