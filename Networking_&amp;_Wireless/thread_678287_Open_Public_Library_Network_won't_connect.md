---
title: "Open Public Library Network won't connect"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by rtrdom on 2008-01-25
My 7.10 Ubuntu on a computer with PRO/Wireless LAN 2100 3B Mini PCI adapter and
RTL-8139 Controller works great in my home network. I can go anywhere in the house
and connect to the D-Link DI-624M router.  However, if I go to the public library and
try to connect to their open, wireless  Netgear WPN 802 v.2 access point, I cannot
connect to either the internet or their network.  I tried pluging a cable from the 
access point directly into the computer and it does not permit internet either. With
only windows installed on the computer, I was able to access their network and thus
the internet.  Changing the manual configuration to
roaming does not help, because everything is greyed out on the manual config page
when enable roaming is checked. Returning to "a not enabled" state requires restablishing the Essid and Address (dhcp).   Does anyone have a suggestion?

Since first posting this, I have discovered that the driver for the ipw 2100 is now present. Now, all I have to do (I think) is to enable
the driver then test it again.  However, I wonder why it works in any room in the house but not at the library. Could it be the difference
between network at home and a necessary wireless connection at the library?
    I have tried every lead I can find over the past 7 days.  The proper driver for the network adapter is present, the lshw -C -network yields:
    

jim@Bravo:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 20
       serial: 00:02:3f:65:1c:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139cp driverversion=1.3 latency=128 maxlatency=64 mingnt=32 module=8139cp multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:68:95:8d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
      ** configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware**=712.0.3:3:00000001 ip=192.168.0.102 latency=128 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
jim@Bravo:~$ 

      It looks to this untrained eye that with things set this way, and either roaming enabled or not, if the machine connects to one
network with out anything happening but turning the computer on, that it should connect to any other network. 
     Can anyone explain why it doesn't connect to the Netgear Access Point but does to the D-link router network?

---

