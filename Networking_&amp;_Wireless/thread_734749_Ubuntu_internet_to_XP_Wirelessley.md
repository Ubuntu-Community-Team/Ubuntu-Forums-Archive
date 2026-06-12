---
title: "Ubuntu internet to XP Wirelessley"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by coldside on 2008-03-25
I've had a quick search but couldn't find anything helpful. 

I'm using Ubuntu 7.10 on a Dell Inspiron 6400 laptop, which the broadband internet cable from the modem connects to. I have a second laptop, a Dell XPS M1710, running XP, with which I want to share the internet connection from the Inspiron wirelessly to the XPS. I have no idea how to go about it. I can share the internet from the XPS to the Inspiron wirelessly when the XPS has the cable, but I can't get it to work the other way around.

HELP!

---

### Post by Paris Heng on 2008-03-25
> **coldside said:**
> I've had a quick search but couldn't find anything helpful. 

I'm using Ubuntu 7.10 on a Dell Inspiron 6400 laptop, which the broadband internet cable from the modem connects to. I have a second laptop, a Dell XPS M1710, running XP, with which I want to share the internet connection from the Inspiron wirelessly to the XPS. I have no idea how to go about it. I can share the internet from the XPS to the Inspiron wirelessly when the XPS has the cable, but I can't get it to work the other way around.

HELP!

To share you Inspiron (Ubuntu) to XPS (Windows) wirelessly, you can done it in [COLOR="Red"]**2 ways**[/COLOR] in the Inspiron (Ubuntu),

1. [COLOR="Red"]**Ad-Hoc mode**[/COLOR], this is the most easy way to share your connection. Just ensure when you in this mode, both the PC must in same frequency ans same SSID in order to work.

> iwconfig <interface> mode ad-hoc
iwconfig <interface> channel <no.> 
iwconfig <interface> ssid <name>

2. [COLOR="Red"]**Master mode**[/COLOR] (I think this can't not be achieved on most of the built-in Wifi NIC), you NIC will become an access point, so you can share your connection to XPS. You can secure you access point with WEP/WPA/WPA2 or even with Radius server!

> iwconfig <interface> mode master

**Noted:** For sharing connection using Ethernet is relatively easy, just connect a crossover cable in both Ethernet ports. Then set your routing table in the Kernel.

Regards

--------------------------------------
[http://parisheng.110mb.com/]("http://parisheng.110mb.com/")

---

### Post by coldside on 2008-03-25
I tried setting it in Ad-Hoc mode on the Inspiron and i recieved these messages.

```
coldside@coldside-laptop:~$ iwconfig eth1 mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not permitted.
coldside@coldside-laptop:~$ 

```


The logical name of my wifi adapter is eth1, at least I think it is. This is what I get when i type
```
sudo lshw -C network
``` into the terminal:

```
 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:d3:96:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:c4:fc:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.2.4 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s

```

The top one is my wifi, the bottom is my ethernet.

---

