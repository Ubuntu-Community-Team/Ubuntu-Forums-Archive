---
title: "broadcom wirless setup help?"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by ttmw on 2008-01-18
Trying to install wirless on my amilo pro v2030 with ubuntu 7.10. and broadcom wirless card(i think) Im a complete noob ain advancend dont know hwat i need to do.

Can someone tell me what drivers i need or what i need to install, thanks in advance

---

### Post by ubutufan on 2008-01-18
Hi and welcome
Go Applications>Accessories>Terminal and type

ifconfig

Post the results and we can take it from there

---

### Post by walkerk on 2008-01-18
Post the results of

```
lspci | grep Network
```
```
lshw -C network
```
```
iwconfig
```

---

### Post by ttmw on 2008-01-18
**ifconfig...**


eth0      Link encap:Ethernet  HWaddr 00:40:CA:DA:93:66   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:20 Base address:0x2000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:3976 (3.8 KB)  TX bytes:3976 (3.8 KB) 

**lspci | grep Network **


00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 

[B]
lshw -C network [/B]

WARNING: you should run this program as super-user. 
  *-network:0 DISABLED     
       description: Wireless interface 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 6 
       bus info: pci@0000:00:06.0 
       logical name: eth1 
       version: 02 
       serial: 00:14:a5:46:9d:e8 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master ethernet physical wireless 
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g 
  *-network:1 
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 78 
       serial: 00:40:ca:da:93:66 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes 

[B]
iw config[/B]
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318" 
          Mode:Managed  Access Point: Invalid    
          RTS thr:off   Fragment thr:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ubutufan on 2008-01-18
You might want to look at an easy install of your wireless driver as posted by compwiz18. He has an excellent guide and you should be in a position to follow his instructions.
His post is the following
[http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom+4318)

---

