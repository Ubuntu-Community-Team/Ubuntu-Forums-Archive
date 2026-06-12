---
title: "Hopeless Wireless :("
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by Th3S\/\/@m! on 2008-10-27
So I've been searching for all the wrong answers to get my Dell XPS Gen 2, running Ubuntu 8.04 LTS. Below is some output, I'm trying to get my wireless nic up and running so I can run Kismet, the main thing is I'm having issues with kismet.conf and I'm not sure how to identify it properly (cause everytime is p00ps the bed. Thanks in advance...



user@aries:~$ sudo lspci -nn | grep Ethernet
[sudo] password for user: 
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet [14e4:165e] (rev 03)
user@aries:~$ sudo lspci -nn | grep Network
03:03.0 Network controller [0280]: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)
user@aries:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
user@aries:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:e5:10:87
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=half firmware=5705-v3.16 ip=10.2.50.104 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:30:f3:f0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes wireless=IEEE 802.11g
user@aries:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MSHOME"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

user@aries:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

