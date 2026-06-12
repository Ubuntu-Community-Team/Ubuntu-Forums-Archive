---
title: "yet another newbie trying to get his wireless card to work....."
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by Tyco on 2008-10-12
Hiya. The title says it all really. My computer specs are as follows:

cpu: 1.8 dual core
mem: 1GB/Go DDR2 SDRAM
HDD: 160 GB/Go
WLAN: 802.11a/b/g

the rest shouldn't matter. I am trying to get my wireless card to work. The wired internet connection works fine (I'm using it now). any advice you give, please bear in mind I am a complete newbie with ubuntu, and will hence probably ask really dumb questions.

basically, any advice?

thanks guys.

---

### Post by Piro24 on 2008-10-12
Well, first off, what card are you using in specific, just saying that your WLAN is using 802.11 a/b/g could mean many different cards, many of which may have different solutions.

However, you may want to try this, as it is really the only way I can think of off the top of my head without any more specific information...

First install NDISWRAPPER, which you should be able to do in a nice graphical frontend from the "Add/Remove" feature under the applications tab. Then, if you kept your windows partition, select the windows driver using the graphical frontend, it's possible that it might work that way. In fact, that's the way I am using for my laptop, since I cannot get my card to work with a native linux driver.

Anyway, before you try this, search around for a native driver to linux with your specific card.

---

### Post by iponeverything on 2008-10-12
If you post the ouput of "lspci" someone here can tell you what if there is a native driver and what it is.  You can also search the forums with the chipset information from lscpi.

---

### Post by Ayuthia on 2008-10-12
If you need to figure out what wireless card you have, please go into the Terminal and type:
```
lspci -nn
```
There should be something that is a Network Controller or Ethernet Controller.  One of them is going to be your wired card and the other one is your wireless.  If you need further help with this, please post the results and we will try to point you in the right direction.

---

### Post by Tyco on 2008-10-18
Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

having conducted the test you advised, this is the wireless card that i am running. well at least it recognises it.........

erm, also I will probably be a little time between replies, as i am not always able to access the internet easily.

anyway, if someone could point me in the right direction that would be great.

---

### Post by mikewhatever on 2008-10-18
That card, Intel Corporation PRO/Wireless 3945ABG, should be working out of the box, without tweaking, ndisrapper, etc. I can also confirm it to support WEP and WPA/WPA2.
Can you please post the output of <sudo lshw -C network>, and tell us more about the network you're trying to connect to.

---

### Post by dpj23 on 2008-10-18
Here's my output it's there just not enabled... Any suggestions would greatly appreciated...


*-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:67:9a:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.52 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

---

### Post by Ayuthia on 2008-10-18
> **dpj23 said:**
> Here's my output it's there just not enabled... Any suggestions would greatly appreciated...


*-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:67:9a:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.52 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

You are going to want to create another thread for your card.  You have a Broadcom card and the original poster has an Intel card.  You will most likely get more responses from others if you place the BCM4306 rev 03 in the title of the post or add it to the keywords.  When you create the new thread, please let us know if you have already installed the firmware (b43-fwcutter or enabled it from System->Administration->Hardware Drivers).

---

### Post by Tyco on 2008-10-20
ah ha. bingo. thanks for your help  guys. thanks to you lot and a little realising I was being retarded on my part, it is now working. Thanks a lot to the lot of ya.....:D

---

