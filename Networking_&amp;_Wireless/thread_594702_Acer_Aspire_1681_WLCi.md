---
title: "Acer Aspire 1681 WLCi"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by windskyrider on 2007-10-28
Hi,

I have Acer Aspire 1681 Laptop and I just recently installed the newest 7.10 Ubuntu Gusty.

Most things work just fine... however, I can't get the WiFi working

here is the message I get from iwconfig:

> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I tried to use txpower to turn on the radio but I got these error message:

> root@WIND:/home# iwconfig eth1 txpower auto
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Input/output error.


And here is my Hardware Detail:

>   *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:76:a6:93
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=172.16.0.7 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:3d:96:aa
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off


Could someone help me out? I heard something about hkacer and I think it's already in the computer... not sure though

Best,

Wind

---

### Post by windskyrider on 2007-10-28
Anyone? Please?

---

### Post by windskyrider on 2007-10-30
Still no one?

I tried:

iwconfig eth1 power on

and

iwconfig eth1 txpower on

Both didn't work.

The button that used to be for wireless radio also doesn't work

Help!

---

