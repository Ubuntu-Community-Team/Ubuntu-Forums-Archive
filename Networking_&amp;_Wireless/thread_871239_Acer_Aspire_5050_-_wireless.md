---
title: "Acer Aspire 5050 - wireless"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by tomst2 on 2008-07-26
OK - I have tried a ton of stuff and still cannot get this wireless to work
here is what I have so far -
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:"2WIRE792"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Encryption key:4918-7426-13   Security mode:restricted
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I had to put the ssid in using iwconfig eth1 essid ... but now this is what it reads.


Also - 
 lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:49:07:ff
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.72 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 01
       serial: 00:30:b4:00:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 driverversion=1.2 latency=80 maxlatency=28 mingnt=10 module=prism54 multicast=yes wireless=NOT READY!

what is the network unclaimed mean - the network unclaimed is the PCMCIA 2wire card that I got from ATT, and how do I assign it to eth1 or how do I get the onboad wireless to work?

Help please

---

### Post by terry slaughter on 2008-07-26
My Acer5102's Atheros wireless shows up as ath0 not eth0.See if you can configure for ath0

---

### Post by tomst2 on 2008-07-26
didnt work

---

### Post by terry slaughter on 2008-07-26
under hardware drivers(sys>admin> hardware drivers)Do you see an entry for Atheros 802.11 wireless lan or Atheros hardware access layer?

---

