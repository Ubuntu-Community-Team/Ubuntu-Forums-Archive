---
title: "Intel WM3945 ABG wireless"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by danex_ali on 2008-07-16
I have an Asus z53S laptop and my wireless card is a Intel WM3945ABG.
The problem is that i think my Ubuntu detects my card as a 4965... i dont really know that for sure but this is the result of:

----------------------------
$ lsmod | grep 3945
(none)

$ lsmod | grep 4965
iwl4965               101480  0 
iwlwifi_mac80211      175112  1 iwl4965

$ lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1d:60:de:2f:03
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A latency=0 link=no module=atl1 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965
----------------------------

-Questions:-

1)Should my ubuntu detect my driver as an 3945 ?
2)Why doesnt?
3)How do i do to fix it ? (how to put my wireless driver to 3945)

I have noticed that when my wireless is on, my card seems to do some weird noise, it sound like sparkels with electricity, something like klick klick klick...

can anyone please help me?
(im on gutsy 7.10)

Many thanks in advance

(sorry for my english :/ )

---

### Post by danex_ali on 2008-07-24
There is nobody that can help me??
or that can explain me something?..... please.....
im very young in the linux world :S

---

### Post by tdeprato on 2008-07-24
I have the same problem.  Any solution yet?

---

### Post by danex_ali on 2008-08-06
Ok, i get it. Nobody wants to help....

---

