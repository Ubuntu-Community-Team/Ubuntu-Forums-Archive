---
title: "Wireless &amp; Acer TravelMate 4500"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by DKJensDK on 2008-02-24
Hi there

Just installed Ubuntu 7.10, but can not get my Wireless internet to work!?! 

I am using a wireless router as accesspoint.

I am no good at computers and hope to get some help from this forum.

With kind regards
Jens

---

### Post by Hightide on 2008-02-24
Hi

can you post output from
 ```

sudo lshw -C network
```


```
sudo iwconfig
```

Also have a quick look at this useful [resources]("http://ubuntuforums.org/showthread.php?t=596797") by Kevdog


regards

:)

---

### Post by anderssl on 2008-04-14
Hey,

I'm having the same problem (with a TravelMate 4501, specifically). Here's my output from the commands above:

sudo lshw -C network:
```

  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:4e:94:81
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.0.150 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:4d:ad:2d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

```
sudo iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"Hyse"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:6161-3131-6262-3232-6363-0000-00   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
Can anyone offer some advice?

- Anders

---

