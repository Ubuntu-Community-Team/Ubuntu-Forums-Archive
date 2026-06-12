---
title: "TEW-443PI(AR5212 chipset) on alternate install doesn't work(yet..)"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by Outrunner on 2007-04-16
Hey there! I wanted to do a barebones install so I used the alternate cd do do a command line only install. Well, while configuring my wireless everything worked fine(done it manually and it said it was successful). But now when I start the system and type ifconfig it only mentions the loopback device. No, the internet doesn't work. Thing is I know that this card works perfectly in both dapper and edgy(but only when installing with a desktop livecd it seems). My kernel version is 2.6.17.10-generic. On a normal desktop install the kernel is newer, so this might have something to do with it(or then again probably not).

I'm willing to try anything really, as long as I get the 'net working... Hopefully I will. Thanks for your time.

---

### Post by josephus on 2007-04-19
can you post 

```
lshw -C network
```

---

### Post by Outrunner on 2007-04-19
There we go.

```
  *-network DISABLED
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller (LOM)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 00
       serial: 00:13:d4:03:a3:9b
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e1000 driverversion=7.1.9-k4 firmware=N/A link=no multicast=yes port=twisted pair
       resources: iomemory:f7de0000-f7dfffff ioport:cf80-cf9f irq:169
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: b
       bus info: pci@03:0b.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:f7ee0000-f7eeffff irq:11

```

---

### Post by josephus on 2007-04-19
does your installation include the linux-restricted-modules-common and linux-restricted-modules-generic (i think that is the name).  i think it probably does, and they are  needed because they include the madwifi drivers for you atheros card.

to load up the driver:

```
sudo modprobe ath_pci
```

---

### Post by Outrunner on 2007-04-19
Nice, I can't believe it was that simple!In case anyone's interested: First I had to use the cd to install linux-restricted-modules-2.6.17-10-generic

To use the files from the cd you need do

```
sudo apt-cdrom add
``` <follow instructions>
then
```
sudo nano /etc/apt/sources.list
``` <comment every line that starts with deb(using #) except the ones that say "deb cdrom:...">

```
sudo aptitude install linux-restricted-modules-2.6.17-10-generic
```

Thanks again for your help.

---

### Post by josephus on 2007-04-19
glad to help

---

