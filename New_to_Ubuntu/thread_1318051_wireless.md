---
title: "wireless"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by thebroken on 2009-11-07
hi, i download ubuntu 9.10, never used another linux before but been thinking about it for a while and thought i would give it a try, i installed it all fine and seems to work very well but i cant get the wireless to work, a friend said to tye into terminal and that i may need drivers, if so what drivers do i need and where do i get them from 

```
sudo iwlist scan 
```and i got this 

```
Lo                                interface doesn't support scanning 
eth0                             interface doesn't support scanning
wmaster0                        interface doesn't support scanning
wlan                             interface doesn't support scanning : nettwork is down
```

i have an acer aspire 3690 with windows XP MCE on it and using that atm 

also could u keep things in as easy as possible as other threads seem like a different language :(

thanks for any help

---

### Post by nothingspecial on 2009-11-07
You need to post your wireless card.

```
sudo lshw -C network
```

---

### Post by thebroken on 2009-11-07
i run that through and got 

```
    chris@chris-laptop:~$ sudo lshw -C network 
    [sudo] password for chris: 
      *-network:0             
           description: Ethernet interface
           product: BCM4401-B0 100Base-TX
           vendor: Broadcom Corporation
           physical id: 1
           bus info: pci@0000:06:01.0
           logical name: eth0
           version: 02
           serial: 00:16:d4:60:12:dd
           size: 10MB/s
           capacity: 100MB/s
           width: 32 bits
           clock: 33MHz
           capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
           resources: irq:21 memory:d0000000-d0001fff
      *-network:1
           description: Network controller
           product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
           vendor: Broadcom Corporation
           physical id: 2
           bus info: pci@0000:06:02.0
           version: 02
           width: 32 bits
           clock: 33MHz
           capabilities: bus_master
           configuration: driver=b43-pci-bridge latency=64
           resources: irq:22 memory:d0002000-d0003fff
      *-network DISABLED
           description: Wireless interface
           physical id: 2
           logical name: wlan0
           serial: 00:16:cf:b7:10:ff
           capabilities: ethernet physical wireless
           configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
    chris@chris-laptop:~$ 
    
```

---

### Post by bkratz on 2009-11-07
There has been a lot written about problems with the 4318, I would suggest going to the networking and wireless forum and using the search function. Here is a good (long!) starting point for you.

[http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm+4318](http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm+4318)

Look at posts 441-444 for testimonials about 9.10 and the guide. you probably have a lot of reading to do.

Good Luck

---

### Post by nothingspecial on 2009-11-07
I have no experience with this card but I beleive you have to install the packages b43-firmware and b43-fwcutter to get it to work.

---

### Post by bkratz on 2009-11-07
> **nothingspecial said:**
> I have no experience with this card but I beleive you have to install the packages b43-firmware and b43-fwcutter to get it to work.



I haven't worked with the card either, but from my reading nothingspecial is correct. Here is a shorter pretty good thread you can probably get what you need from or post on the end of.

[http://ubuntuforums.org/showthread.php?t=993193&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=993193&highlight=bcm4318)

Also you might want to check under menu system---administration--hardware drivers and see if you need to enable a driver.

---

