---
title: "Default Wireless Card"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by almo5t on 2008-09-26
Hello Ubuntu forums, 

Since I have installed Ubuntu 8.04, I have been having a persistent problem with the speed of my internet (just on Ubuntu).  I believe that I have narrowed down the problem.  I figured that the wireless card that is supposed to be used is not; but, rather, another wireless card is being used. 

```
*-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:46:15:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.102 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:db:db:93
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes

```

I believe that my laptop should be using the top wireless card, however when I run iwconfig, I receive this message.

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"***"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:28:A3:8D   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=100/100  Signal level=-52 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have tried to set up the wireless network by following this threadhttp://ubuntuforums.org/showthread.php?t=684495

I go to connect through the command line, and I receive an error message saying something to the effect of dhclient can not be set because a ; was expected at the end of line 14 and 19.  I will try to post the exact message, and I would do it now but the process kicks me off the internet. Does anyone have any help that they can offer me? It would be very much appreciated.

Thanks in advance.:)

---

### Post by willca on 2008-09-26
Well it seems you are not associated with any hotspot.

whats the output for this and point out which hotspot you like to connect to...

sudo iwlist wlan0 scan

---

### Post by mikewhatever on 2008-09-26
It looks like PRO/Wireless 4965 is the only wireless card present. What's the other one?

---

