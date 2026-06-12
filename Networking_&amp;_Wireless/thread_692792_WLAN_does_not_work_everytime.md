---
title: "WLAN does not work everytime"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by thetones on 2008-02-10
im using gutsy 7.10 with a TP-link wn321g usb wireless adapter.  i did all that ndiswrapper stuff and it works.  but it doesn't work everytime i boot linux.  it's inconsistant and everytime i boot my pc it sometimes works and sometimes doesnt.  

ideas?

---

### Post by Hightide on 2008-02-10
hi thetones

can you post output of

lshw -C network

iwconfig

go to Applications\accessories\terminal

if you want to clarify what the commands do put man in front of them 'man lshw -C network and press Q to exit.

as i am going out to work now, you may want to have a look at Kevdog's wireless [tutorial]("http://http://ubuntuforums.org/showthread.php?t=571188") 


regards
:)

---

### Post by thetones on 2008-02-12
this si the output code:

```
god@node02:~$ sudo lshw -C network
[sudo] password for god:
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:4a:a1:47
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:e0:87:82:bf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
god@node02:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

god@node02:~$ lsusb
Bus 002 Device 002: ID 13ba:0017  
Bus 002 Device 004: ID 04e8:3419 Samsung Electronics Co., Ltd 
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 1976:6025  
Bus 001 Device 009: ID 2164:2507  
Bus 001 Device 007: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 001 Device 006: ID 148f:2573 Ralink Technology, Corp. 
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp. 
Bus 001 Device 001: ID 0000:0000  
god@node02:~$ 


```

---

