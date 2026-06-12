---
title: "Network manager keeps disconnecting"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by dknoppix on 2007-07-08
I have Ubuntu Feisty installed and the network manager connects to my network via WPA.

I have two wireless cards installed on here, and one of them is internal and doesn't work, but the network manager keeps on trying to reconnect via the internal card. 

Is there any way I can disable the internal card?

Thanks,

dk

---

### Post by kevdog on 2007-07-08
If we unload the driver module or blacklist the driver module, then I think this will solve your problem.

Can you list

lshw -C network

Please post the above, and tell me looking at the output which device is your internal wireless device.

---

### Post by dknoppix on 2007-07-08
```
danny@danny-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:0b:db:05:17:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=32 maxlatency=10 mingnt=10 multicast=yes
       resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
  *-network
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@07:00.0
       logical name: wifi0
       version: 01
       serial: 00:13:46:c3:bc:b2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.2.4 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:40000000-4000ffff irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:7b:36:30
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 multicast=yes wireless=IEEE 802.11b
```

The last one on the list (eth1) is the internal. The atheros is my working one.

Thanks!

---

### Post by dknoppix on 2007-07-16
Help please?

---

### Post by ugm6hr on 2007-07-18
> **kevdog said:**
> If we unload the driver module or blacklist the driver module, then I think this will solve your problem.
If this is true, try this (it adds *blacklist orinoco* to etc/modprobe.d/blacklist file):
```
echo 'blacklist orinoco' | sudo tee -a /etc/modprobe.d/blacklist
```

However, I have an AR5005G (internal in my laptop) - and the issue with recurrent disconnections with Network Manager and WPA is known (can't remember where - but it's mentioned in launchpad somewhere).  Apparently, Network Manager re-scans available networks every now and then, and the interaction with madwifi / WPA causes this to drop the connection for a few seconds.  It automatically reconnects though.

The only solution I could find for this was to use Wicd instead (and uninstall Network Manager):
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Just make sure you edit the Wicd Preferences: 
> WPA supplicant driver: wext
Wireless interface: ath0

---

