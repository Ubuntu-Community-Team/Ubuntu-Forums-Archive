---
title: "Wireless not functioning"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by mickeywilson5 on 2011-05-18
My wireless works fine with mint 10, but with ubuntu 11.4 nothing....only a wired connection shows and i have already installed the STA driver but it is still not recognized. What is the problem here? Also i have downloaded ndiswrapper...still nothing...so is it when i use linux 10 on the same laptop my wireless works but with ubuntu it does not? What to do?

---

### Post by 3xp10r3r|X13 on 2011-05-18
[FONT=Courier New]mint and ubuntu are two different operating systems (I know that you know that :) )

So ubuntu might not support the hardware mint supports.

I know, this didn't help, but it's just a suggestion...


PS: your saying that it works fine with other distributions so the lack of hardware support is probably it
[/FONT]

---

### Post by jerome1232 on 2011-05-18
> **mickeywilson5 said:**
> My wireless works fine with mint 10, but with ubuntu 11.4 nothing....only a wired connection shows and i have already installed the STA driver but it is still not recognized. What is the problem here? Also i have downloaded ndiswrapper...still nothing...so is it when i use linux 10 on the same laptop my wireless works but with ubuntu it does not? What to do?

What chipset is it?

```
sudo lshw -C network
```

ps. The above poster, I can barely read your font. It's so thin

---

### Post by josepharari on 2011-05-18
[http://www.linuxquestions.org/questions/linux-newbie-8/how-can-i-install-a-driver-on-my-dell-1545-wi-fi-880607/](http://www.linuxquestions.org/questions/linux-newbie-8/how-can-i-install-a-driver-on-my-dell-1545-wi-fi-880607/)

try this

---

### Post by wep940 on 2011-05-18
If you can temporarily hard-wire a connection to your router, you could try the following with ubuntu:
 
Back out anything you have done - ndiswrapper, blacklist, STA driver installation, etc., to get back to a clean state (or just reinstall 11.04 if you can).
 
sudo apt-get update
 
Then go to system/administration/additional drivers (might say restricted drivers?).  It will connect to the net and try to locate a driver.  If it does and one shows in the list after this completes, enable that driver.

---

### Post by mickeywilson5 on 2011-05-19
It is still a no go.  Now, under connections it does not even have enable wireless. Just wired connection. When i use the sudo lshw -C network command.....it only shows
*-network               
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:c7:8d:38
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.4 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:c0300000-c0301fff

---

### Post by jerome1232 on 2011-05-19
Well then you have a BCM4311, should work with STA drivers from what I'm reading. If you hardwire you computer with an Ethernet cord, and do as described above (using restricted drivers) you should get Internet access.

Here is a community doc about how to install those drivers, it seems you can use an Ubuntu install cd to do it as well.

good luck.

If the STA driver fails, I would first suspect everything else you have tried, you can also try ndiswrapper with some windows drivers to get it working

---

