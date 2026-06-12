---
title: "[SOLVED] Atheros trouble"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by zotamis on 2008-08-27
I have a dlink DWL-630 atheros chipset, and im having a bit of trouble.  Im rather noobish so I appologize in advance.

I think I installed the madwifi drivers, I did the following

sudo apt-get install linux-restricted-modules madwifi-tools

it installed everything, so I ran iwconfig and got

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:2592  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I dont now if the card itself is working or not, because I cant find any networks.  any suggestions?

---

### Post by zotamis on 2008-08-28
hmm, still cant figure it out.

---

### Post by dhysk on 2008-08-28
when you do iwconfig i believe you should get ath0 and wifi0

the madwifi-tools isn't actually the driver from what i understand but a set of tools to help you configure it.

try this [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

you may want to d/l the driver off off the madwifi site instead

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz) 

the one used in that tutorial may be specific to his chipset

if i find anymore info i will post it sorry I couln't help anymore it's been awhile since I've had to get madwifi working.

---

### Post by zotamis on 2008-08-28
dyhsk, thanks for the info.  Like I said im a newb and im still learning.  Ill give that a shot, but im terrible w/ tarballs, ive never suscessfully installed software from one.

But ill give it a shat, Thanks in advance

now  lets seee.......

---

### Post by zotamis on 2008-08-28
I tried what you said, and well nothing happened.  I still see no networks when I go into "Wireless Networks"

I typed iwconfig and got

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:4866  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Blackcabs on 2008-08-28
> **zotamis said:**
> I have a dlink DWL-630 atheros chipset, and im having a bit of trouble.  Im rather noobish so I appologize in advance.

I think I installed the madwifi drivers, I did the following

sudo apt-get install linux-restricted-modules madwifi-tools

it installed everything, so I ran iwconfig and got

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:2592  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I dont now if the card itself is working or not, because I cant find any networks.  any suggestions?

The old madwifi drivers are already on your system..can you type lshw -C network into a terminal and post us the output please,, as it will give us more information

---

### Post by zotamis on 2008-08-28
Blackcabs, here is the output

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:5c:38:a3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:11:95:49:fd:fb
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.103 latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


BTW thanks for helping me guys. I really appreciate it :)
This problem might be from PEBKAC, so who knows....

---

### Post by Blackcabs on 2008-08-29
> **zotamis said:**
> Blackcabs, here is the output

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:5c:38:a3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:11:95:49:fd:fb
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.103 latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


BTW thanks for helping me guys. I really appreciate it :)
This problem might be from PEBKAC, so who knows.... 

Ok it looks like you have the correct driver installed, are you using Network manager to automatically set up this card or are you trying to set it up manually.And do have your own wifi access point that is close to you ??

---

### Post by zotamis on 2008-08-29
> **Blackcabs said:**
> Ok it looks like you have the correct driver installed, are you using Network manager to automatically set up this card or are you trying to set it up manually.And do have your own wifi access point that is close to you ??

Blackcabs, Yes i have a router in a room next to mine.

Your other question, Ok what do you mean "set up" the card?  Ill tell you what I did and we can go from there.

I went to  SYSTEM > ADMINISTRATION > NETWORK
there is a option for Wireless Connection, i click propeties
and I fill out my network info I type in my network name and 10 digit wep

and I cant access any webpage.

So is there a better way to setup a card? or do you have to do it like that?

---

### Post by Blackcabs on 2008-08-29
> **zotamis said:**
> Blackcabs, Yes i have a router in a room next to mine.

Your other question, Ok what do you mean "set up" the card?  Ill tell you what I did and we can go from there.

I went to  SYSTEM > ADMINISTRATION > NETWORK
there is a option for Wireless Connection, i click propeties
and I fill out my network info I type in my network name and 10 digit wep

and I cant access any webpage.

So is there a better way to setup a card? or do you have to do it like that?

Yes there is a much easy way..clear all those settings so they are blank and tick the allow roaming checkbox and close it..Now open a terminal and type nm-applet when you do this 2 small tv's will appear at the right on your top tool bar,,, right click on them and make sure that the enable networking and enable wireless options are ticked.. Next the tv icon will change into a swirling circle as it looks for access points,,find yours from the list,,tick it and follow the quotes.

Let me know how you get on

---

### Post by zotamis on 2008-08-29
Blackcabs, ok so im connected to my network now.  there are 2 signal strength bars on the top bar.  

I cant access any webpage yet, im going to fool around with the settings.

Ok I have no IP adress or anything, but it says im connected to the network

update:  I restarted, the network isnt liking my wep key

update2: YAAAY!! I LOVE YOU Blackcabs, I got my wireless to work!!
you have been sooooo helpful!!!  Ill buy you a beer!

---

### Post by Blackcabs on 2008-08-29
No problem Im glad i could help, just tick the thankyou star for me

---

### Post by zotamis on 2008-08-29
Done!! Like 40000 times!

---

### Post by Blackcabs on 2008-08-29
Re: Atheros trouble
Blackcabs, ok so im connected to my network now. there are 2 signal strength bars on the top bar.

I cant access any webpage yet, im going to fool around with the settings.

Ok I have no IP adress or anything, but it says im connected to the network

update: I restarted, the network isnt liking my wep key

update2: YAAAY!! I LOVE YOU Blackcabs, I got my wireless to work!!
you have been sooooo helpful!!! Ill buy you a beer!

---

### Post by Blackcabs on 2008-08-29
Im gonna send you a pm

---

### Post by Blackcabs on 2008-08-30
Lovely

---

