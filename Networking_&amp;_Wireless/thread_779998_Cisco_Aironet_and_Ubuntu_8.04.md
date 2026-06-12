---
title: "Cisco Aironet and Ubuntu 8.04"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by mendelbenjamin on 2008-05-03
Hello guys, my wireless worked with previous versions of Ubuntu but after I installed it today it isn't anymore. I am currently running Ubuntu 8.04 on a IBM T41.

It doesn't show up at the Network Settings but I can see the wifi interface with lshw. Anyone knows how to fix this? Thanks in advance. 

mendel@mendel-laptop:~$ sudo lshw -C network
[sudo] password for mendel: 
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:7f:ee:8c
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=N/A ip=192.168.1.104 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list
       configuration: driver=airo latency=64 maxlatency=4 mingnt=4

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
irda0     no wireless extensions.

---

### Post by chili555 on 2008-05-03
See here, post #9. Worked for me. [http://ubuntuforums.org/showthread.php?t=409247](http://ubuntuforums.org/showthread.php?t=409247)

---

### Post by mendelbenjamin on 2008-05-03
w00t! Thanks, it also fixed my sound problem.

---

