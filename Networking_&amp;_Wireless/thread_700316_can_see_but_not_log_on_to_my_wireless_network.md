---
title: "can see but not log on to my wireless network"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by familjen on 2008-02-18
Hi, I have a peculiar problem. I have posted in the end of some threads before but no one answeared so I state my problem in a fresh thread instead. 

My problem: I can not use the internet when logged on to my unprotected wireless network. I use the program wifi-radar that says that I recieve an ip-adress but I still can not see any other of the computers in the network and I do not get up on the internet. However can I log on to my neighbours unprotected wireless network and use the internet and when I type this I do it from a wired connection on my access point and then I also see all the other computers (which are wired). 

I previously used xubuntu with a wireless connection to the same access point flawless. 

anyway 


>>iwconfig  
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

>>lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:cb:c3:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 ip=192.168.0.30 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:12:9d:d9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

help is really appreciated

---

### Post by familjen on 2008-02-18
Hi again, 
I might add that when I am logged on to my network then the result of "iwconfig" is:
>>iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"nowire"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:95:20:05:DD   
          Bit Rate=11 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=72/100  Signal level=-55 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Where nowire is the name of my network. But I do not see any of the other computers or are able to reach the internet.
/familjen

---

