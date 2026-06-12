---
title: "wireless problems on an acer aspire 5570z"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by tzenda on 2010-04-13
just installed ubuntu 9.10 and updated all the packages with my wired conection. the wireless connection connects but is supper slow and falls off all the time. 

the laptop is an acer aspire 5570z, not sure all the specs on it but if u tell me how to get the hardware manager to display all the stats i will post em up to help with the diagnossis.

 i did some searching on the forums but the solution i found was for a different aspire and didnt work.

its been a long time since i used Linux and it might take me a few tries to remember things, i used to use debian.

---

### Post by ajgreeny on 2010-04-13
To show your wireless adapter card make etc etc, run the command ```
sudo lshw -C network
```

---

### Post by tzenda on 2010-04-16
k here is the output from that, i tried a few things from the info but it still doesnt work. back to the drawing board :(

i am up for sugesstions


  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:61:83:49
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.26 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:44000000-44003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7e:9b:23:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:44100000-4410ffff

---

