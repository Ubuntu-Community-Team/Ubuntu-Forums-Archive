---
title: "Problems with wlan driver"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Gerde on 2009-11-03
Hello everybody,

I installed ubuntu yesterday on my old notebook ( toshiba satellite l10). Everything except of the wlan works fine.
I installed the winxp driver using ndiswrapper.
ndiswrapper -l says:
> neti2220 : driver installed
device (17FE:2220) presentBut it doesnt show up.
sudo lshw tells me
>      *-network:1 UNCLAIMED
                    description: Ethernet controller
                    product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
                    vendor: Linksys, A Division of Cisco Systems
                    physical id: 4
                    bus info: pci@0000:02:04.0
                    version: 00
                    width: 32 bits
                    clock: 33MHz
                    capabilities: pm bus_master cap_list
                    configuration: latency=64 maxlatency=32 mingnt=32
                    resources: ioport:3c00(size=32) memory:e0401c00-e0401c1f memory:e0401000-e04017ff
    iwconfig:
>     thomas@thomas-laptop:~$ iwconfig
    lo        no wireless extensions.
     
   
  eth0      no wireless extensions.
    
I searched the forums and did find some interesting threads, but nothing seemed to work. Hope someone can help me.

Gerde

---

### Post by blazemore on 2009-11-03
1) Create dependency file
```
sudo depmod -a
```

2) Load ndiswrapper module
```
sudo modprobe ndiswrapper
```

3) Load automatically on boot
```
sudo ndiswrapper -m
```

---

