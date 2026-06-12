---
title: "Wireless Connection Failure BCM4312 (rev01)"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Sibko on 2008-12-10
Hello everyone,
OK second Try...](*,)

[COLOR="DarkOrange"](DV2815nr BCM 4312 (rev 01 | Ubuntu 8.10 intrepid | Kernel 2.6.27-9)[/COLOR]

This is what i get with the wl.ko installed and still does not work.
My latest try was sing b43fwcutter and using Wicd 1.5.3, still the connections is not established it only wait to be assign an ip. 
In regards to the router everything it;s perfect, i use another pc to connect to try it and it works.


root@Esma:~#  lshw -C network
 ```

  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:0d:f4:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ba:46:83:e1:a8:83
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Please help! I use this pc to work and i wont fall into buying an external pci all because Microsoft and BroadCom want to hold hands together making contracts that only force users/people to use there OS.:evil: too bad i only had money for a refurbished hp.

---

### Post by newbee70 on 2008-12-10
> **Sibko said:**
> Hello everyone,
OK second Try...](*,)

[COLOR="DarkOrange"](DV2815nr BCM 4312 (rev 01 | Ubuntu 8.10 intrepid | Kernel 2.6.27-9)[/COLOR]

This is what i get with the wl.ko installed and still does not work.
My latest try was sing b43fwcutter and using Wicd 1.5.3, still the connections is not established it only wait to be assign an ip. 
In regards to the router everything it;s perfect, i use another pc to connect to try it and it works.


root@Esma:~#  lshw -C network
 ```

  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:0d:f4:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ba:46:83:e1:a8:83
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Please help! I use this pc to work and i wont fall into buying an external pci all because Microsoft and BroadCom want to hold hands together making contracts that only force users/people to use there OS.:evil: too bad i only had money for a refurbished hp.

it would have been nice if you would have given the whole output instead of editing out the first 1/2.

What driver shows up if you go into System / Administration / Hardware drivers?

---

### Post by Sibko on 2008-12-10
So this is my last post where i describe the problem broadly.
[http://ubuntuforums.org/showthread.php?t=1005862](http://ubuntuforums.org/showthread.php?t=1005862)

this is all the code that showed up:
```

root@Esma:~#  lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:6e:66:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.101 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:0d:f4:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:a6:fd:ed:78:82
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

The drivers that appear in hardware drives are: BROADCOM STA wireless driver, but they are deactivated.-
But i also tried the wl drivers and did work either.
Thanks !!!

---

