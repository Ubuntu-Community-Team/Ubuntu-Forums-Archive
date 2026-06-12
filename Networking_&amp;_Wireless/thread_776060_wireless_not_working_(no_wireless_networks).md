---
title: "wireless not working (no wireless networks)"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by firas66 on 2008-04-30
Hello,
I'm a newbie in this whole Ubuntu thing. I just installed ubuntu 8.04 and right off the bat my wireless card isn't seeing any wireless network. I tried to manually enter the essid, however It just shows the wireless network with 0% signal (i tried pinging to see if there actually was a connection but timeout). it's an open wireless network no wep or wpa. I know that the card isn't malfunctioning, because it worked flawlessly in windows.

I guess i should post the  lshw -C network results:

firas@firas-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:5c:64:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:12:21:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.2.146 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
firas@firas-laptop:~$ 

please someone tell me what to do to get it working.

---

