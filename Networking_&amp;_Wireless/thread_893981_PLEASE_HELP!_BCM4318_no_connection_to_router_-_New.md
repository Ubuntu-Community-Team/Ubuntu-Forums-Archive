---
title: "PLEASE HELP! BCM4318 no connection to router - Newbie to Ubuntu"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by Astro-Pilot on 2008-08-18
Hi all.

I am completely new to Linux operating systems and have just installed Ubuntu 8.04 two days ago.

Ubuntu, in my opinion, is far better than Windows Vista, which I have installed on a second partition on my Dell Inspiron 530.But there is a slight problem.

I can't connect to my router. :confused:

This is why I have come here, to the Ubuntu community for some aid.

I have read many HOWTO's ,tutorials, support pages, etc., but every one I came upon was too complex for me to understand, as I am more used to MS-DOS than a terminal; (as I have started using Ubuntu only two days ago)

My problem is that I have a Broadcom BCM4318 (rev 02) wireless card that came included with my Dell Inspiron. 

The card works flawlessly in Windows Vista, but for some reason when I go into System> Administration> Network, and configure the Network settings by hand, no connection is established by my card.

So far, using ndisgtk, the graphical frontend for NDISwapper, I have managed to use a .inf file from a Windows x64 driver for the BCM4318 card. I know this is the correct driver for one, I am using the amd64 version of 8.04, and two, in ndisgtk, it says Hardware Detected.

My card does not have defects as Ubuntu and Windows can detect it, and using a command in Terminal, (I forget which one) I managed to learn that the drivers were in use. 

If anyone can help me in a newbish, non-complex way to help me fix this issue, I would extremely thankful!

Also, I have tried installing b43-fwcutter, but since I have no internet connection whatsoever, (wired is not possible as I am not the administrator of my router and the router is too far away) I have been unsuccessful.

Please help and thanks a bundle in advance!

---

### Post by falcon61102 on 2008-08-18
Could you go into the terminal, run and post the results of:
```
lshw -C network
```

That will display your hardware info relating to your network card(s).

---

### Post by Astro-Pilot on 2008-08-18
Sure thing.

```
 *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:8c:c7:90
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.2.0 firmware=1.1-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:60:be:18:66
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.116 multicast=yes wireless=IEEE 802.11g
```

---

### Post by falcon61102 on 2008-08-18
It looks like you problem may be that you need the hardy bug fix.  Ubuntu 8.04 Hardy Heron has a bug with these cards and there is a simple work around for it.  

Here is HowTo that works well with fixing this.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix)

If you have any questions or get any erros, post here and we'll be able to help.

---

### Post by Astro-Pilot on 2008-08-19
Falcon, thank you so much for your help. 

The module is now listed as ndiswrapper, and my network card on the back of my PC has the light on, which must indicate it is working, because before I used this fix, it wasn't. 

But I do need one more bit of help if you don't mind. When I try to connect to the internet using Firefox, I gives me the error page, when there is no connection to the internet. Is this due to my manual network settings, and if you can help me fix it and get a working connection to the internet, please do, and thank you so much!

Here is the present code presented now with terminal by using 'lshw -C network' :
```
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:8c:c7:90
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.2.0 firmware=1.1-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1d:60:be:18:66
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 ip=192.168.0.116 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

---

### Post by falcon61102 on 2008-08-19
Even though you have the card working, you need to connect to a network before the internet will work.  You should have an icon in the upper right hand corner of your screen, the Network Manager.  You should be able to click on that and see the available networks now.  Once you connect then you should be able get online through firefox.

---

### Post by Astro-Pilot on 2008-08-19
Falcon, thank you. You are the BEST!

I finally got my internet working after 3 sleepless nights!

My connection is up and running because of you!

Once again thank you so much for your time and support. :guitar:

---

### Post by falcon61102 on 2008-08-19
No problem, glad you got it working.

---

