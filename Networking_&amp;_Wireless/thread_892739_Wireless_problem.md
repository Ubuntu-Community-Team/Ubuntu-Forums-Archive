---
title: "Wireless problem"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by suprakid24 on 2008-08-17
I just downloaded the latest ubuntu the other day, and it is now installed on my computer. My wireless picks up my router, shows the little bars for signal but there is no connection, the bars arn't filled. It's a WPA encrypted signal, but I turned that off to test it and the same thing happend. I am plugged into a wire right now so I can search for stuff, but so far no solution. 

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:cf:dc:33
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
       serial: 00:16:d3:18:77:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.2.7 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes


Any help would be great, thanks :)

---

### Post by suprakid24 on 2008-08-17
I did some more searching and found a solution...

[http://ubuntuforums.org/showpost.php?p=5608332&postcount=2](http://ubuntuforums.org/showpost.php?p=5608332&postcount=2)



/thread.

---

