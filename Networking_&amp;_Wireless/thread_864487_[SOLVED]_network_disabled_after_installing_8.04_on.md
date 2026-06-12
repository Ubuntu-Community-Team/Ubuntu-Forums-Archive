---
title: "[SOLVED] network disabled after installing 8.04 on a amd64"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by old farmer on 2008-07-19
SOLVED  just reinstall 7.10, wireless works




wired network works
however wireless doesnt
here is some info:

$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0             
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 2 
       bus info: pci@0000:08:02.0 
       logical name: eth0 
       version: 10 
       serial: 00:16:36:95:83:a1 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.102 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes 
  *-network:1 
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 4 
       bus info: pci@0000:08:04.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:16:cf:91:5b:dd 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 

$ sudo iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan0     Interface doesn't support scanning : Network is down 

$ lspci -nn |grep BCM 
08:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 

$ iwconfig wlan0 
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 


can anyone help
Thanks

---

