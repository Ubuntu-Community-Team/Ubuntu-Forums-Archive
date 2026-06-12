---
title: "How can I configure an Ethernet interface that does not exist?"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by Halbarad on 2008-08-26
Hardy 8.04, Asus Z53H.
I tried to configure my network interface eth0 using Network Tools -- and I got the reply that my interface does not exist. It does a lot of work for an inexistent interface, because everything but Transmission works fine and smooth -- Internet, samba-sharing with file down/uploading etc. Network Tools also displays a good amount of data about my inexistent interface: IP Address, Broadcast, Hardware address, statistics about transmitted and received bytes, 0 errors, and so on.
I have issued the basic commands:

```

$ sudo ifdown eth0
ifdown: interface eth0 not configured
~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
```

On the other hand, lshw an lspci give:

```

~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:92:4a:b3:67
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:1a:92:4d:e6:84
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

~$ lspci | grep Ethernet
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

About the Wireless: it is there, it seems to work, but I don't have a wireless router and can't use it.
My router is a Linksys BEFW11S4.

I have been able to fix other problems by reading the documents and the forum threads through: but this problem about the ghost eth0 is tougher. If anyone could help, I'd be grateful.

---

### Post by Sam Lars on 2008-08-26
Could you do a 
```
ifconfig
```
to see what you're interfaces are up to?

---

### Post by Halbarad on 2008-08-26
Here it is:

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:4d:e6:84  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe4d:e684/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:124422959 (118.6 MB)  TX bytes:6162440 (5.8 MB)
          Interrupt:18 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102682 (100.2 KB)  TX bytes:102682 (100.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:92:4a:b3:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:fdffc000-fe000000
```

There is another fact that might be related to the non-existence of the interface. If I try to set a static IP via Network Settings, all the network and internet stop working. That is, if I disable the roaming mode and set IP to 192.168.1.80 (this is an address the router would not assign to the other PCs in the network, because it starts from 192.168.1.100), mask to 255.255.255.0 and Gateway to 192.168.1.1.
I mean, if this prob is not related to the interface inexistence, let's drop it.

---

### Post by Sam Lars on 2008-08-26
That's weird, it seems to be there, but Network Tools says it isn't?
The static IP could be related, but I'm not sure.
You mentioned that Transmission wasn't working well... is this what you're trying to fix, or are you just perplexed at the non-existent thing?

---

### Post by Halbarad on 2008-08-26
I enclose a scaled screenshot of the Network Tools message. 
I don't really have a concern about Transmission -- Deluge works very well (btw, isn't it funny? something works perfectly, other things that one would regard as roughly equivalent don't work at all...) My main reason is that I'd like to understand and know more. And, sure, I'd like to be able to set a static IP and to master this field... (a better understanding and control of the system was my main reason for abandoning the Microsoft stuff :) )

---

### Post by Sam Lars on 2008-08-26
It's definitely odd sometimes when one thing works and you think another thing should but doesn't... that goes for all OS's, though.
It is nice with Linux that you can have a much better understanding to work those things out (or someone else that does).

I thought of something.  Check your /etc/network/interfaces.  I get the same behavior of ifup/down that you do for my wlan0, which is not in that file at all (I'm using Network Manager).  I think those commands are primarily for use based on that file.
When does the error for Network Tools pop up?  When you select wlan0?  I have no problem with mine...

---

### Post by Halbarad on 2008-08-27
Thank you so much for your help. I'm sorry for replying so late... I have been sleeping (yeah, it's a luxury but I can afford it... sometimes).
I entirely agree with you about Linux -- I have definitely moved to it, for many reasons.
My /etc/network/interfaces is quite short:

```
auto lo
iface lo inet loopback
```

The error with Network Setup pops up when I select eth0 -- that is, the wired network.

---

### Post by Halbarad on 2008-08-27
Uh oh -- Reading again your post, I thought I should check whether the roaming mode is sort of incompatible with an approach via ifup etc. In fact, this is more or less the way things stand. I've eventually found the documentation I needed:

[https://help.ubuntu.com/community/NetworkAdmin]("https://help.ubuntu.com/community/NetworkAdmin") and
[https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager]("https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager")

Briefly, Network Settings (that is, network_admin)
> "is an alternative to using nm-applet (GNOME front end for NetworkManager)".
According to the document, Network Manager (that is, nm-applet)
> does not use the standard NetworkAdmin file /etc/network/interfaces to store the Wireless Network settings, so you will not be able to use ifup and ifdown commands to start/stop network adapters. This can make it more difficult to diagnose connection problems. 
:tongue: It truly can!!! -- A suggestion for Intrepid (or for Jiggling John): if a user starts Network Tools while Network Manager is running, notify her that Network Manager is in charge -- or that the interfaces in roaming mode cannot be configured. This would be much better than claiming they do not exist!

I don't know if this will be enough to solve my problems with the static IP or with Transmission -- but I can give it a fresh start. Thx a lot, Sam Lars! :biggrin:

---

