---
title: "Wireless Trouble!"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Arnitak on 2007-11-03
I have installed a Ubuntu 7.10 on a Acer 5315 with a "Broadcom 4311" and have trouble using the wireless module. The Card is seen by the kernel as eth1. I try to manually change the options using the man pages and iwconfig since configureing the card from the desktop does not work at all. In manual mode all the values are set, except one.

Access Point: Invalid.

I try auto, off, and the AP MAC Address. It does not work at all? Can anyone help me pls? It's my only link to the net with the laptop.

---

### Post by kevdog on 2007-11-03
Can you post the following:

iwlist scan

---

### Post by Arnitak on 2007-11-03
The lo and eth0 don't support scanning. 
The eth1 prints no scan results.
I tried to scan in windows vista and succesfully scanned several networks.

Any ideas?

---

### Post by kevdog on 2007-11-03
What does lshw -C network say about the eth1 device.

---

### Post by kevdog on 2007-11-03
Just curious -- what driver are you using or how did you setup your wireless card!

---

### Post by Arnitak on 2007-11-03
This is my current configuration.

  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:2b:19:62
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1c:26:5c:88:22
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

The driver is installed out of the box, the card currently is set in roaming mode, the info above was taken with that roaming mode active. I took it of from roaming mode, enterd the values manually, like the essid and other stuff and that was it. It did not worked, then I tried to do the same thing from the console only this time using iwconfig.
What should I do?

---

### Post by Arnitak on 2007-11-03
From the log it seems that the card is disabled, since it is in roaming mode. How do I enable it? And what is this roaming mode? I took it off, entered manual mode, entered options, but it appears it is still disabled!

---

### Post by kevdog on 2007-11-03
Try typing 

sudo ifconfig eth1 up

And then check lshw -C network and make sure the info states it is not DISABLED.

---

### Post by Arnitak on 2007-11-03
The ifconfig eth1 up retuirned a very very interesting error considerin its a fresh copy of ubuntu.

SIOCSIFFLAGS : No such file or directory

Any ideas?

---

### Post by kevdog on 2007-11-03
Do a search for SIOCSIFFLAGS in the forums.  I saw a thread about this about 1-2 weeks ago and the guy used some method to solve his problem.  I cant seem to remember the solution.

---

