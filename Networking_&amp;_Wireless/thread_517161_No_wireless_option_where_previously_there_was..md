---
title: "No wireless option where previously there was."
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by Bajoran Rogue on 2007-08-04
I installed Ubuntu yesterday, when it was able to connect to wireless. Today it failed to connect to the internet and so I went to try to start the connection again but there is no option under Networks, or Networking; I forget what it is called as I am using the Windows partition right now.

I think that it mentioned something about a proprietary driver yesterday if that is any help.

Also, from the following I think that there is a driver.
> sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 12
       serial: 00:0a:e4:bb:5a:b5
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:d2000000-d2003fff ioport:2000-20ff irq:16
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:d4000000-d4000fff irq:17

 sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by spd106 on 2007-08-04
You are right about the restricted driver, open up the Retricted Drivers Manager from the System -> Admin menu and make sure that the Intel card is enabled.

---

### Post by Bajoran Rogue on 2007-08-04
Thank you for your help, though I didn't get a chance to try it out. The wireless seems to have decided by itself to start working again. Under the Restricted Driver Manager it is enabled now, but I didn't do anything. 

At least it is working again now; I'll remember your advice if it starts acting up again. Thanks.

---

### Post by Bajoran Rogue on 2007-08-05
It stopped working again, and I lost the Wireless option, however the driver is enabled under Restricted Drivers Manager.

---

