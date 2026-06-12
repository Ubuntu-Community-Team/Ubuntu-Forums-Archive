---
title: "airnet AWU154 not working"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by dagarshali on 2008-10-19
Hi,
I am absolutely new to linux..I have installed ubuntu on my laptop. The laptop is fairly old (thinkpad T23). I am not sure how to find what installation and what kernel is installed on this system. Its ubuntu 7.01 gutsy. Where do i find this info.

I installed ndiswrapper package and the gui interface for that. I had the cd for the wireless adapter and I copied the driver corresponding to the windowsXP and then pointed the .inf file for the gui of ndiswrapper.

when I go to the terminal and type /usr/bin/lsusb, this is what i get

```
root@dagarshali-laptop:/home/dagarshali# /usr/bin/lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0457:0163 Silicon Integrated Systems Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

But once i install the driver, if i hit the configure network button, 
the only options that I see are wired connection and modem

Also, when i try the lshw -C network I get this
```

root@dagarshali-laptop:/home/dagarshali# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 41
       serial: 00:d0:59:ab:4f:b1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.0.5 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
```

I really have not idea how to get this to work .Any help would be greatly appreciated.

I normally connect to the wireless router via a WEP key

Regards,
vishwa

---

