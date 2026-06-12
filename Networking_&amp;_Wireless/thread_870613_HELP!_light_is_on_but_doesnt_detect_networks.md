---
title: "HELP! light is on but doesnt detect networks"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by env2156 on 2008-07-26
I did a clean install of xubuntu this is my 2nd day im still a noob,  im using a Presario R3000 with a infamous broadcom b43 wireless driver.
It says the hardware is enabled but I can only connect to the internet through wired connection cant connect wirelessly. Iv tryed almost everything I got ndisgtk thing installed but i dont know where to find the inf file and i also installed the b43fwcutter. Also to add my Blue light stating my wifi is on stays on i cant turn it off. The network iv been trying to connect is not password protected

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo lshw -C network:

*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:04:46:a0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.7 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:5a:de:9d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


this forums one of my last hopes iv spent alot of hours trying to figure this out. i hope someone can help

---

### Post by lisati on 2008-07-26
Does your wireless network show up when you enter ```
iwlist scan
``` from the terminal?

---

### Post by env2156 on 2008-07-26
thats a no 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by env2156 on 2008-07-26
ok so i was able to find the inf file and installed it and i redid the iwlist
got this [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation

but im still not detecting any wireless connections

---

### Post by superprash2003 on 2008-07-26
try following this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) and do a reboot

---

### Post by env2156 on 2008-07-26
> **superprash2003 said:**
> try following this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) and do a reboot

YES!!! success thank you so much iv been killing myself trying to find the solution you are my jesus thanks alot for pointing me the right direction

---

