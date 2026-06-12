---
title: "Wireless Help Please"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by riles32807 on 2008-06-07
Hi I just did a fresh instll of Ubuntu Stuido and I'm having trouble connecting to both my wireless & wired ethernet.  I'm not exactly a stranger to linux but it's been a while and I've forgotten much of what I knew.  I'm not sure where to start but here's what I've found so far. 


Network Connection dropdown shows
lo
eth1:avahi

lo shows idle
and eth1:avahi shows error

when I type in eth1, however it shows a connection with a signal strength, but I can't web-brows etc.  I assumed that this was because WEP isn't set up, but when I go to configure it pops up with "the interface does not exist.  Check that it is correctly typed and that it is correctly supported by your system."

lshw returns
>  *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0 DISABLED
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 01
                serial: 00:c0:9f:56:df:71
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no module=ssb multicast=yes port=twisted pair
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:2a:ae:c2
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

Sorry I don't have more info, but any help would be greatly appreciated.

---

### Post by superprash2003 on 2008-06-07
could you please post your ifconfig and iwconfig output from the terminal

---

