---
title: "Ubuntu, Torrent, driver or hardware problem?"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by Havok_CR on 2007-06-22
Hello dear Ubuntu community :D
This is my first post, it is the first time I ask for help because I can often find the answers in UbuntuForums threads or googling a while.
Anyway, I hope you could help me.

This is my problem:
Now I'm using my Wireless connection, no problems, I can stay connected and surf the web for hours without problems, I can suspend the system, wake-it up and Ubuntu reattaches me to my wireless home network. Nevertheless, when I start some kind of torrent-client, for example BitTorrent or FrostWire (I tried both), after 5 or 10 minutes my connection dies, a message globe appears: "Se han desconectado de la red" (You were disconnected from the network). I mean, It really dies, my wireless hardware does not detect wireless networks any more (but my wireless hardware is still "visible"), and if I restart the system, Ubuntu shows me that the only hardware I own is the ethernet card and not the wireless card. In other words, the Wireless card "disappears". 
The only way I could "reactivate" the hardware was booting in Windows Vista (System bundled with my PC.... anyway... ¬¬) and no wireless hardware is detected, so I need to restart the machine again and re-enter Windows Vista :S The second reboot in Vista "reactivates" the hardware, so, now I can restart in Ubuntu and use my wireless connection for 5 - 10 minutes more (if I use torrent-clients, if I use Firefox I can stay connected for hours).
I know it is terrible, but some times it get worse : the wireless network dies too. Except that this time the solution is easy, I just need to restart the router (this issue happens 1/6 of times).

I list the hardware :

1. When I'm connected:

```
havok@Havok-PC:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:d5:c2:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

2. When I start a torrent client and the hardware dies:

```
havok@Havok-PC:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:d5:c2:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

You can see the big DISABLED

3. When I restart Ubuntu after the issue:
```
havok@Havok-PC:~$ sudo lshw -C network
havok@Havok-PC:~$
```

Just nothing :S

My computer is a HP Pavilion SlimLine s3020n (AMD 64 Athlon X2 Dual Core 3800+, 1GB ram).
I'm not sure of the manufacturer or version of my wireless card (some hint about how to know?).
I'm using Ubuntu 7.04 FeistyFawn
My router is a Zoom X4.

Any idea?
Thanks in advance.

:popcorn:

---

### Post by spd106 on 2007-07-05
This wiki page should help in identifying your card
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I'm surprised that the driver was not listed in the lshw command output, it usually is.

---

### Post by imadb on 2008-05-05
Hi there,
I'm having the same problem, I have tried all torrent clients (transmission, ktorrent, azureus). When any torrent client is running, my network dies, it takes firefox 3 for ever to load a page. Shutting the torrent client off, things get back to normal speed. I had fresh install ubuntu 8.04, didn't have this problem with 7.10. Here is the description of my network hardware:

-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 02
       serial: 00:0a:e4:5c:ed:32
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.254.1 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

Any help will be very much appreciated.

---

