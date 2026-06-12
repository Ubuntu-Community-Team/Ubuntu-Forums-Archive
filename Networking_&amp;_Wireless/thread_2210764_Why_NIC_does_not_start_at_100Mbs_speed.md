---
title: "Why NIC does not start at 100Mb/s speed"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by ivanovic.marko on 2014-03-12
I have two laptops, one is very old (IBM x30) and runs puppy linux with kernel 3.2.18. Another one is older laptop but it has 32bit 1.8GHz dual core processor and 2GB of DDR2 RAM (which should mean, much younger but also old). It runs Ubuntu 12.04 LTS with kernel 3.2.0-60-generic-pae.
When I plug in cable to older laptop it connects to network immediatelly and it works on 100Mb/s. But Ubuntu laptop takes quiet time to start connecting (it connects quickly, but it takes him time to realize that have plugged cable in, and it's same cable and same device on the other side).

This is output of "sudo lshw -C network" on Ubuntu laptop:

```
  *-network               
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: LSI Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 00:40:45:31:62:55
       size: 100Mbit/s  <-- this is after I do command below, 10Mbit/s on start up
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=et131x driverversion=v2.0 duplex=full ip=192.168.1.157 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 memory:fd800000-fd9fffff memory:fdae0000-fdafffff
```

when I do this:
```
sudo ethtool -s eth0 speed 100
```
it responds with:
```
Cannot advertise speed 100
```
Then it disconnects form network and than connects again only this time speed is 100Mbps. So that is what I want, but can set this command to rc.local? I mean, does this negative response (altough results are OK) means that it's not very smart to do?
And why it doesn't start at 100Mpbs in first place?

---

### Post by chili555 on 2014-03-12
et131x ??!!?? I never heard or saw one of these before!> but can set this command to rc.local? I mean, does this negative response (altough results are OK) means that it's not very smart to do?Yes you can and you should. This is a rather unusual problem, so we can't tell you much more without examining logs, experimenting, etc., etc. However, I'd put the line, without sudo, in rc.local and reboot a couple of times. If it works as expected, I'll call it a successful day!

---

### Post by ivanovic.marko on 2014-03-12
OK thanks.
Without sudo, of course :)
I'll let you know in 5 min if it works

---

### Post by ivanovic.marko on 2014-03-12
It works.
Thank you.

---

### Post by chili555 on 2014-03-12
Please use thread tools at the top to mark Solved. That way, the three other et131x cards on the planet can find the solution!

---

### Post by ivanovic.marko on 2014-03-20
Sorry, but I can't mark it as solved. First two times after restart it worked. So I tought it still works. But it does not. I really makes me mad. It would be much better if it didn't work at first place. I tried putting the command in other files that are executed at start up, but it doesn't help.
I also have this strange problem with wireless. Wireless networks are getteing detected much faster then ethernet. So after I boot it connects to wireless network even if I have cabel plugged in. And if I don't have cabel plugged in at start up, and then I disconnect from wireless, and plug cabel in, it takes at least 30 seconds for computer to realize it.

---

### Post by chili555 on 2014-03-20
> So after I boot it connects to wireless network even if I have cabel plugged in.You may be able to stop that by editing connections in Network Manager and, under Wireless, un-checking connect automatically.

Let's see if there is any clue in the logs:```
dmesg | grep -e eth0 -e et131x
```

---

### Post by ivanovic.marko on 2014-03-21
Here it is. But now I've removed "upstart" conf file and put  the ethtool command back in rc.local, and now it's back on 100Mbps.

[   30.969950] et131x: module is from the staging directory, the quality is unknown, you have been warned.
[   30.986685] et131x 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   30.986704] et131x 0000:01:00.0: setting latency timer to 64
[   31.308846] et131x_eth_mii: probed
[   31.308980] et131x 0000:01:00.0: attached PHY driver [Generic PHY] (mii_bus:phy_addr=100:00)
[   42.432553] device eth0 entered promiscuous mode
[   43.202250] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   74.316746] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   84.512049] eth0: no IPv6 routers present

It was also at 100Mbps first time I rebooted after putting the ethtool command to upstart conf file. This method seems like one shoot. I'll post output after I restart again.

---

### Post by ivanovic.marko on 2014-03-21
After I rebooted again it was 100Mbps. But then I unplugged the cabel and then I plugged cabel in again, and after 30 or more seconds it realized that cabel is in and it connected. But it was again 10Mbps. It's really frustrating. :)

Here is output:

[   32.564769] et131x: module is from the staging directory, the quality is unknown, you have been warned.
[   32.585508] et131x 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.585608] et131x 0000:01:00.0: setting latency timer to 64
[   32.878067] et131x_eth_mii: probed
[   32.878195] et131x 0000:01:00.0: attached PHY driver [Generic PHY] (mii_bus:phy_addr=100:00)
[   44.112069] device eth0 entered promiscuous mode
[   44.201330] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.880726] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   57.952051] eth0: no IPv6 routers present
[   80.302497] device eth0 left promiscuous mode
[   80.884205] et131x 0000:01:00.0: Link down - cable problem ?
[   82.597017] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   82.884839] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   93.208038] eth0: no IPv6 routers present
[   96.884393] et131x 0000:01:00.0: Link down - cable problem ?
[  101.273681] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  182.885259] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  193.776076] eth0: no IPv6 routers present

---

### Post by ivanovic.marko on 2014-03-21
Thank you for trying to help me, I appreciate it.

---

### Post by chili555 on 2014-03-21
I am not sure there is an answer that is manipulable by the user. In many drivers, there are parameters that can be set by users. They are listed in *modinfo*. Here is a random example from my ethernet driver:> parm:           eeprom_bad_csum_allow:Allow bad EEPROM checksums (int)
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)If there was a parameter to load for your driver, we could write a conf file to say, roughly, options et131x please default to 100Mb/s=Y or some such. However, there is no parameter at all available in your driver:```
$ modinfo et131x
filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/staging/et131x/et131x.ko
description:    10/100/1000 Base-T Ethernet Driver for the ET1310 by Agere Systems
license:        Dual BSD/GPL
author:         Mark Einon <mark.einon@gmail.com>
author:         Victor Soriano <vjsoriano@agere.com>
srcversion:     03763BB81758A8525E3C788
alias:          pci:v000011C1d0000ED01sv*sd*bc*sc*i*
alias:          pci:v000011C1d0000ED00sv*sd*bc*sc*i*
depends:        
staging:        Y
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
```I notice these notes, as well:> staging:        YAnd in dmesg:> et131x: module is from the staging directory, the quality is unknown, you have been warned.In this context, staging means that the driver works pretty well but is not yet fully matured.

I can suggest two things; first, that you register and file a bug: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Second, this is a pretty rare device. I suspect it is sparsely developed. You might consider a different network card.

---

### Post by ivanovic.marko on 2014-03-22
OK, thank you.
I don't need full speed all the time. So when I do need I'll start script like this:
#!/bin/bash
gksudo ethtool -s eth0 speed 100 duplex full

---

