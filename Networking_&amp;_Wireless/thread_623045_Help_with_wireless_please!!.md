---
title: "Help with wireless please!!"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by Mr cracker on 2007-11-25
Hi! 
I'm having a problem with my Intel PRO/Wireless 2200BG 802.11 b/g WLAN card. 
It used to work with the version 7.04, but when i upgraded to 7.10 it stopped working. 
i've tried using NDiswrapper, ive instaled the .inf file. it says that the hardware its present but i still cant connect.!!
I dunno what i should do!, im a newbie to Ubuntu. ITs drivin me crazy!!!! :mad:

Here's the output for:  _sudo lshw -C network_


```
*-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:0e:7b:71:36:1f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.69 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

```


THANKS FOR UR HELP!

---

### Post by spd106 on 2007-11-26
I'm not very familiar with Intel cards, but as far as I know it uses the ipw2200 driver. So try this command to see if it's loaded.
```
lsmod | grep ipw
```

If you get no results then try loading it like this
```
sudo modprobe ipw2200
```

You may also need to use the Restricted Drivers Manager as this card requires some non-free software to work.

---

