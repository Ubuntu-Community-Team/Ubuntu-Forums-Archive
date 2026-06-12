---
title: "Dlink PCMCIA WN1330 Configuration Help"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by rokytnji on 2008-07-20
I have a Dlink PCMCIA WNA 1330 card with Atheros Chipset . Can't get it to connect because of my lack of skills. I am posting these screen shots to show where I am at so far. Any help on what I am doing wrong would be appreciated. I will be sitting here in the wheelchair for hours if need be awaiting your knowledgeable advice with bated breath.

---

### Post by JagDragon on 2008-07-20
Judging my your screenshot of lspci, you seem to have both an Intel and an Atheros wireless card. That can't be helping.

Try "Enabling roaming mode" and seeing if NetworkManager catches on.

---

### Post by rokytnji on 2008-07-20
Have done as you ask. LED on dlink card is still blinking like before. communicating using land line on laptop. Also have desktop on line in case i need it. Still not connecting.

---

### Post by rokytnji on 2008-07-20
Here is the screen shot of Network Tools.

---

### Post by JagDragon on 2008-07-20
Have you tried looking up in the top right hand corner of the screen and clicking on something that looks like two monitors?

---

### Post by rokytnji on 2008-07-20
Yes, I have. With the land line I have Enable Networking checked. Enable Wireless checked, Connection information shows up,Edit wireless settings shows up. 

Land line disconnected I get everything the same except connection information is greyed out.

---

### Post by JagDragon on 2008-07-20
Hmm. Try taking one of your cards offline. In a terminal,```
ifconfig
``` should show you all of the cards you have, and ```
iwconfig
``` should show you which of those are wireless. Take one of them offline with ```
sudo ifconfig [interface] down
```For me, that would be ```
sudo ifconfig wlan0 down
```

---

### Post by rokytnji on 2008-07-20
Here is the screenshot of iwconfig command

---

### Post by JagDragon on 2008-07-20
so run ```
sudo ifconfig eth1 down
```

---

### Post by rokytnji on 2008-07-20
I don't know what to insert for interface command. I probably should disable eth 1 but I can't tell what to put in interface from the text in the page. Would it be eth 1?

Didn't see your reply till I replied.

---

### Post by rokytnji on 2008-07-20
Here is the latest screenshot after entering sudo ifconfig eth1 down. The screen shot is the latest from iwconfig.

---

### Post by rokytnji on 2008-07-20
Do I hear crickets chirping?

---

### Post by rokytnji on 2008-07-20
Here is the readout for sudo lshw -C network

harry@harry-laptop:~$ sudo lshw -C network
[sudo] password for harry: 
  *-network               
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:9
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:80:45:29:3f:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.3 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
       serial: 00:15:00:10:0a:ce
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:15:e9:d9:31:9d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

### Post by rokytnji on 2008-07-20
This is how far I have gotten with dlink card unplugged and using intel chipset to try to connect.


	
Ok this is where I am at now

harry@harry-laptop:~$ iwconfig eth1 essid harrybelkin
Error for wireless request "Set ESSID" (8B1A) :
SET failed on device eth1 ; Operation not permitted.
harry@harry-laptop:~$ sudo iwconfig eth1 essid harrybelkin
[sudo] password for harry:
harry@harry-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit ISC DHCP

Listening on LPF/eth1/00:15:00:10:0a:ce
Sending on LPF/eth1/00:15:00:10:0a:ce
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by rokytnji on 2008-07-20
Still no wireless connection.

---

### Post by rokytnji on 2008-07-20
bump....



@#$%&*@ it.

---

### Post by rokytnji on 2008-08-01
Problem resolved. Wireless working now using Intel internal PCI wireless A/B/G card running with Intel Linux Driver.

---

