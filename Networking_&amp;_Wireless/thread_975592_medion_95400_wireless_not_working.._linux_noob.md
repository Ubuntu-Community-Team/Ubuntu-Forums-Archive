---
title: "medion 95400 wireless not working.. linux noob"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by nostradamus2000 on 2008-11-08
Hi, I finally installed ubuntu 8.10 on my Medion MD95400 laptop, from Aldi, but the wireless doesn't work. I have found out that i have got a Intel Pro Wireless 2200BG card. i already been able to get the laptop to detect the card, yet when i run iwconfig the following appears.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr=1600 B   Fragment thr=2304 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


normally in windows i have to push a hotkey to turn wlan on yet in ubuntu this doens't work.

if annyone got a solution fore this bigg thx in advance.

---

### Post by charliebrownau on 2009-03-25
I have the ALDI/Medion 97160 and have the same issue with Ubuntu 804

I will be trying Debian 5 soon and seeing if it supports the 
Azurewave rt2860  802.11n Wireless LAN Card

---

### Post by Svenare on 2009-04-09
The medion wireless switch works differently to most other laptop,
you need software that only works in windows to turn it on and off.  
I've been looking for a solution for years....and now i have it.

The about a week ago I found something in bios.  
under advanced, there was an option "wireless" which was set as "disabled", 
I simple changed it to the other option "last state" and bam! I can use wireless in Ubuntu

hope this helps

---

