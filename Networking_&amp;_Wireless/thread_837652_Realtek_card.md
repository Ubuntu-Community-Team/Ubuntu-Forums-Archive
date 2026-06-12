---
title: "Realtek card"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by jenova_skill on 2008-06-22
I found all the info on how 2 fix my wireless networking problem.... some patch for 64bit ubuntu but u have to compile it urself..... being the noob i am i can't figure out how it's done.....   
SO here is my info of my card and i'd like some intructions on a Wrapper driver  ( i got the concept )  

jacob@Jacob-laptop:~$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:81:76:3e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.103 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

---

### Post by jenova_skill on 2008-06-22
BTW THe wireless COnnections just arent showing up On the connection manager............ I have no option to enable wireless connections or nething .... Im able to connect hard wired but thats it...... I have 32bit version of ubuntu on The same laptop but older version of it and it workes just fine.....

---

