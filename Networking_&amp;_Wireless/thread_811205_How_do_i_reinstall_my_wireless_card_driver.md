---
title: "How do i reinstall my wireless card driver"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by tropdoug on 2008-05-28
Hi guys, 

somehow I lost my wireless capabilities whilst trying to correctly enable my nvidia drivers. I did 
```
 lshw -C network 
```

and got this returned

```
kim@laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:a0:d1:68:56:1a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-5 ip=10.1.1.7 latency=0 module=e1000 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
kim@laptop:~$
```As you can see the  PRO/Wireless 3945ABG Network Connection is unclaimed.

When I go to system>admin>restricted drivers manager I find a driver that has not existed before. Its listed as an IPW3495 (see attachment) but whilst enabled is not in use. 

I think this must have appeared when I reinstalled the nvidia-glx-new package as a dependancy maybe. But it definately was not there when my wireless was working ok. 

Anyone got any suggestions?

---

