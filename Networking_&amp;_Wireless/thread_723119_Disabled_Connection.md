---
title: "Disabled Connection?"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by perito on 2008-03-13
PLEASE HELP ME GET THE INTERNET CONNECTION
im  trying to connect to my rounter with WPA ency
I think its not getting the IP address via DHCP
so I did this
sudo lshw -businfo

got this
```

           *-network 
                description: Ethernet interface 
                product: 88E8039 PCI-E Fast Ethernet Controller 
                vendor: Marvell Technology Group Ltd. 
                physical id: 0 
                bus info: pci@0000:02:00.0 
                logical name: eth0 
                version: 14 
                serial: 00:a0:d1:79:09:cb 
                capacity: 100MB/s 
                width: 64 bits 
                clock: 33MHz 
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair 
        *-pci:1 
             description: PCI bridge 
             product: 82801G (ICH7 Family) PCI Express Port 2 
             vendor: Intel Corporation 
             physical id: 1c.1 
             bus info: pci@0000:00:1c.1 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list 
             configuration: driver=pcieport-driver 
           *-network DISABLED 
                description: Wireless interface 
                product: PRO/Wireless 3945ABG Network Connection 
                vendor: Intel Corporation 
                physical id: 0 
                bus info: pci@0000:03:00.0 
                logical name: eth1 
                version: 02 
                serial: 00:1b:77:3b:93:b4 
                width: 32 bits 
                clock: 33MHz 
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated 

```

is *-network DISABLED the problem?
how to enable it? coz in the network setting it is Enabled ...

---

### Post by NorthernLights on 2008-03-13
Do you get any error message when connecting with Network Manager ?

---

### Post by Paris Heng on 2008-03-13
Check your **/etc/network/interfaces**, the dhcp should be enable on the your wireless interface. I think should be eth1 is this case. Most of the time Intel NIC is run-able in Ubuntu.

---

