---
title: "Wireless problem in ubuntu !"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by YMI on 2008-08-14
Hi everyone . 


Actually i'm having problem with wireless conf I try many time to configure my wireless network but unfortunately i couldn't .

1 - i installed Ubuntu in Macbookpro . 
2 - 802.11n 
3 - I have one option under (system --> Administration --> wireless network driver . I enable this option but i still couldn't configure it .

It still gave me this message when i try to install any driver 
(Not a valid driver .inf file )
4 - I'm using version 8.04 . (the latest) . 

And the last Q  is how to enable hot key ? 

I really appreciate ur support .


Waiting for ur feedback ....^_^

---

### Post by YMI on 2008-08-14
This might help ..

root@yazeed-laptop:~/ndiswrapper-1.49# lshw -C network 
  *-network UNCLAIMED     
       description: Network controller
       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 13
       serial: 00:1b:63:b1:19:bf
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.9 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s

---

### Post by YMI on 2008-08-14
Thanks guys i already solved my problem by add the radar from 
system --> administration --> synaptic package manager .
And don't ask me about the driver because i installed a lot of drivers ^_^.

---

