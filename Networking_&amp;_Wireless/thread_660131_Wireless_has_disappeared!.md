---
title: "Wireless has disappeared!"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by huggies15 on 2008-01-06
ok, i searched for similar problems, but couldnt find anything... if there is i apologise

i have an acer aspire 5620, with gutsy on it... all has been good, been using the net via wireless for a year (inc. feisty time) and no problmes, been moving houses, finding wireless and everything is good.

i took the laptop on holiday with me - there was no wireless access there anyway, waste of time - and i come back and now gutsy wont recognise the fact that i have wireless, i can an lo and eth0 from ifconfig but nothing for the wireless (used to be eth1).

apart from changing the time on the laptop - and back again- i have done literally nothing to any settings, nothing has been installed or uninstalled, so i dont know what has happened?!

it happened once before when i was dual booting with windows and i had to reinstall windows drivers before it worked, i had somehow mucked them up in windows and ubunut wouldnt then work. but this time is different, i only have ubuntu on it, so dont know what has happened.

if someone has some ideas on how to refind my wireless adaptor woudl be v. grateful, dont have time atm to reinstall everything!!!

Cheers
huggies15

---

### Post by Vadi on 2008-01-06
Try doing **sudo ifconfig eth1 up**, does wireless show up on **iwconfig** then?

---

### Post by huggies15 on 2008-01-06
i get an error: error while getting interface flags: no such device

it seems like the os isnt seeing the wirelessdevice at all

---

### Post by Vadi on 2008-01-06
Are you using ndiswrapper for wireless?

Also, do **sudo lshw -C network**, what does it report?

---

### Post by sheepfunk on 2008-01-06
I hope this isn't bad form, jumping into someone else's thread, but I'm having the same issue, and when I run sudo lshw -C network, I get the following. 

 *-network               
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:13:a9:f1:19:04
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.101.106 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

I noticed that the hardware address is missing from the wireless interface.

---

### Post by huggies15 on 2008-01-06
im not using ndiswrapper, it used to work "out-the-box"
will try the other command in the morning, but if the fact im not using the wrapper makes some iffenrece please keep leaving comments

---

### Post by huggies15 on 2008-01-07
*-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:16:36:2b:95:7e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=32 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s


thats what came out... hope it means something to someone

---

### Post by huggies15 on 2008-01-08
bump this up again, maybe someone will have an answer

---

