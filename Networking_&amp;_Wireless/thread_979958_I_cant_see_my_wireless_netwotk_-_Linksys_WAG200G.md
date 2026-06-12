---
title: "I cant see my wireless netwotk - Linksys WAG200G"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by dimis80 on 2008-11-12
Friends I am facing a weird problem...

I have wireless router in my home (WAG200G) connected wired to my desktop WinXP and wireless for my laptop (hp 6720s).
In my previous installation of ubuntu (edubuntu 7.10) my wireless was working flawless...
3 days ago i have installed ubuntu 8.10 on my laptop.
When i was searching for my wireless network i couldn't find it!!!
i can see though wireless spots from around my neighbor, except mine...

I tried to:
Free the wireless network (no pass)
Change the security (WEP, WPA etc.)
Make a manual connection...

but nothing really happen..

Now i am on Internet with a spot from my neighbor but i need mine!

If this looks familiar to any of you please help me...:confused:
many thanks...

==========================================================================
root@mitsakos-laptop:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:4b:65:5f:47
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:bc:d5:3f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.65 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:f6:30:01:83:6a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

