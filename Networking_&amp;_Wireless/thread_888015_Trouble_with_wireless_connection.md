---
title: "Trouble with wireless connection"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by ThoGe on 2008-08-12
I am working with Hardy Heron on an Acer Extensa 5220. For my wireless connection I would like to use the Belkin wireless G USB Adapter with a FritzBox 3170 router. Unfortunately I always loose the wireless connection around 5 to 10 seconds after I started the connection and I am asked for my WPA network password again. I am sitting with my notebook next to the router. My wired connection causes no problems.
Details about my configuration is shown below with lshw and iwconfig. 
Does anybody know what might be wrong? Is it possible to use the built-in Broadcom card with Hardy?

lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:0a:f5:8e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 ip=192.168.178.20 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1e:4c:40:be:c5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan2
       serial: 00:1c:df:35:c3:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+blkwgu driverversion=1.52+Belkin Corporation.,06/01/2 multicast=yes wireless=IEEE 802.11g
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan2     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by pytheas22 on 2008-08-12
There are a few things that could be going on.

First, it could be Network Manager screwing up the connection.  Using [wicd]("http://wicd.sourceforge.net") instead might help.

If not, you could look at the output of:
```

dmesg
```

after the connection drops.  It will hopefully give some clues as to what's going on, which could be a bug with ndiswrapper, or some wpa_supplicant problem.

If you want to get the Broadcom card working (yes, it should work fine on Hardy), that might be easier than trying to deal with the other card.  I think (but could be wrong; there are so many Broadcom chipsets and unfortunately no good list of which driver supports which model) that 94311 doesn't work well with the b43 or bcm43xx drivers (the native Broadcom drivers), but ndiswrapper should support it well.  There are good instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") that cover your card.  If you go this route, be sure to pay attention to the "Hardy Bug Fix" section (it's not really a bug, but it does need to be fixed).

---

### Post by ThoGe on 2008-08-13
Excellent! Thanks for your quick and good support. I followed the instructions on your suggested page for getting the Broadcom card working. There were no problems and I am working wireless now. I did not follow the Belkin USB Adapter approach for now, but I will try this in the next days. Thanks!

---

