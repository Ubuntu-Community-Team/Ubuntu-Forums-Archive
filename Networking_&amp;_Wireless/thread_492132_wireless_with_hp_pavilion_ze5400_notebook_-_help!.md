---
title: "wireless with hp pavilion ze5400 notebook - help!"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by Helix. on 2007-07-04
I am completely new to Ubuntu 7.04. I have used previous versions in the past on a different computer.

After that other computer crashed, I was given a hp pavilion ze5400 laptop. I have ubuntu installed, but I cannot connect to my wireless network.

On the bottom it says "Broadcom BCM94036MP", so I guess that must be the wireless card.

Please help!

Thanks

---

### Post by Helix. on 2007-07-05
I don't mean to bump my topic,  but I really need help on this...

---

### Post by Perfex on 2007-07-05
This is what I find [http://ubuntuforums.org/showthread.php?t=446010&highlight=ze5400](http://ubuntuforums.org/showthread.php?t=446010&highlight=ze5400) hope it helps

---

### Post by Helix. on 2007-07-06
Didn't work...thanks for helping though

Here is some more info...see if anybody can make any sense of it

> helix@pavilionze5400-ubuntu:~/firestarter-1.0.3$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


> helix@pavilionze5400-ubuntu:~/firestarter-1.0.3$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning : No such device


> helix@pavilionze5400-ubuntu:~/firestarter-1.0.3$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth1
       version: 02
       serial: 00:0b:cd:74:9d:8b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d0002000-d0003fff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:aa:6b:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.107 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:2400-24ff iomemory:d0006000-d0006fff irq:10


---

### Post by Helix. on 2007-07-06
I fixed it! :p

If anybody has a pavilion ze5400, type this into the terminal:
```
lspci | grep Broadcom\ Corporation
```

You should get this. If not, this topic doesn't apply to you ;)

> 00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


Now, follow ALL instructions to the letter: [http://ubuntuforums.org/showthread.php?t=201902&highlight=Broadcom+4306]("http://ubuntuforums.org/showthread.php?t=201902&highlight=Broadcom+4306")

...and your done! ;)

---

