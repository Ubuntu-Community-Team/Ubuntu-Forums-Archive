---
title: "Noob needs help setting up my wifi card"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by x NZERO x on 2008-05-21
I just installed the latest Ubuntu 8.04 and I can't seem to get my wireless card to work. I have looked at some howto's on how to get it going but can't seem to get anywhere. 

lspci | grep Broadcom\ Corporation shows
04:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

lshw -C network shows
*-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: eth0
       version: 10
       serial: 00:e0:4d:45:47:df
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0f:66:1b:90:4e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Now I put in my essid name and my key and all that under connect to another wireless connection. It shows signal bars on the top right of the screen. When I move the mouse over it, it says wireless network connection to 'my essid' (0%). I have know idea what to do from here.

---

### Post by x NZERO x on 2008-05-21
ok I got my wireless card to see my network but I can't seem to get a ip address it still will say it is connected. Can anyone help me. I have tried WPA, WEP, and open. with no luck.

---

### Post by mapes12 on 2008-05-22
Did your machine work with wireless under 7.10?

Have you got an ethernet cable plugged into your machine?

Please can you post the output to:

```
ifconfig
```

---

