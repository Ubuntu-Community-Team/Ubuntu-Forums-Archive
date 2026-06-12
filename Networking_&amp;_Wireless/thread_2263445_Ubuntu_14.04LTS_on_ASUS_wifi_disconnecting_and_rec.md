---
title: "Ubuntu 14.04LTS on ASUS wifi disconnecting and reconnecting"
date: 2015-02-01
forum: Networking &amp; Wireless
---

### Post by Daniel_Ortega on 2015-02-01
Hi im a beginner and started out with replacing my operating  system with ubuntu 14.04. It was working fine until recently nothing  that I know of has been changed. When I use 

rfkill list i get: 
0: phy0: Wireless LAN soft blocked: no hard blocked: yes 
1: asus-wlan: wireless lan soft blocked: no hard blocked: no 
2: asus-bluetooth: bluetooth sb:no sb:no

  
when i close my laptop lid and reopen it, the wifi connects to the  network and shows that it is not hard blocked anymore. Any help or  suggestions would be appreciated.

  
iwconfig gives me 

eth0: no wireless extensions; lo:no wireless  extension; wlan0: IEEE 802.11bgn power management is  off.

  
when i run 

lspci -vnn | grep Network i receive: 
02:00.0 Network  controller [0280]: Ralink corp. RT5390 wireless 802.11n 1T/1R PCIe  [1814:5390]

  
and time is kinda important,not that anyones elses time isnt  important, and i know i was stupid for this but i installed this on my  laptop i use for school and work and need it for monday.

I do not know if this is something but noticed alot of asus computers builtin wireless are having problems running ubuntu 14.04 wired connection works fine.

---

