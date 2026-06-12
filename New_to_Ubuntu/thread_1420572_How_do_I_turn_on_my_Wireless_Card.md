---
title: "How do I turn on my Wireless Card?"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by beber on 2010-03-03
[COLOR=black][FONT=Verdana]Hi guys, what a great forum, please forgive me if I'm posting this in the wrong place. However, I just installed Ubuntu last night and I have never used Linux before, so I consider myself to be an "Absolute Beginner"[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Here is my problem, the install went fine but and Ubuntu recognizes my wireless card, however it shows up as "Disabled". Under the Help topics it says that my wireless card is turned off and to simply turn it on. When I press the wireless button on my laptop nothing happens, the light does not turn on.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Can some one tell me what I need to do.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks for the help.[/FONT][/COLOR]

---

### Post by Peter09 on 2010-03-03
Can you post the output of the terminal commands
```
ifconfig
```
and
```
lshw -C network
```

---

### Post by beber on 2010-03-03
I'm at work now, I'll try when I get home tonight.  Thanks

---

### Post by bkratz on 2010-03-03
> **beber said:**
> I'm at work now, I'll try when I get home tonight.  Thanks

If this is a Dell you might also want to post the output of

rfkill list

---

### Post by beber on 2010-03-03
> **bkratz said:**
> If this is a Dell you might also want to post the output of
 
rfkill list
 
 
Its an HP

---

### Post by julianb on 2011-06-13
I'm running a Compaq presario with Lubuntu 11.04 and the wireless doesn't seem to be switched on. iwconfig gives lo and eth0 with "no wireless extensions" and doesn't show wlan0. The broadcom sta wireless driver (which seems to be the right one) is installed and activated (using "additional drivers").

output of the command lshw -C network:

```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:20800000-20803fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:45:5c:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=69.139.18.165 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff

```

any ideas?

---

### Post by VOT Productions on 2011-06-13
Check the BIOS is it enabled. Also, try **ifup wlan0**.

---

### Post by zero244 on 2011-06-13
On my HP laptop all I had to do was install the proprietary drivers on the install cd. Which Ubuntu will do for you.
Ubuntu 10x through 11.04 automatically recognised my broadcam wireless adapter.

Look at the top of the screen and see if the driver icon is there.

---

### Post by gandaran on 2011-06-13
> **julianb said:**
> I'm running a Compaq presario with Lubuntu 11.04 and the wireless doesn't seem to be switched on. iwconfig gives lo and eth0 with "no wireless extensions" and doesn't show wlan0. The broadcom sta wireless driver (which seems to be the right one) is installed and activated (using "additional drivers").

output of the command lshw -C network:

```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:20800000-20803fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:45:5c:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=69.139.18.165 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff

```

any ideas?
maybe the STA driver isn't the right one, do you have any other option in additional drivers?
or type broadcom in synaptic package manager search box and read the information on the drivers available.

---

### Post by julianb on 2011-06-13
There were no other suggestions in "additional drivers".

however, in synaptic there was one search result that seemed like it might work:
b43-fwcutter (Utility for extracting Broadcom 43xx firmware)

Will find out if that works.

---

### Post by wildmanne39 on 2011-06-13
> **julianb said:**
> There were no other suggestions in "additional drivers".

however, in synaptic there was one search result that seemed like it might work:
b43-fwcutter (Utility for extracting Broadcom 43xx firmware)

Will find out if that works.Hi here is a link to help you get your card working which is the 4311.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

