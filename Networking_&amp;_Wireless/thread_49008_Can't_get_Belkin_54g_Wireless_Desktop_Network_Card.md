---
title: "Can't get Belkin 54g Wireless Desktop Network Card (F5D7000) Rev 03 to work"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by Sune Simonsen on 2005-07-14
I just got a Belkin 54g Wireless Desktop Network Card (F5D7000) Rev 03 PCI card, the 
[ndiswrapper](http://http//ndiswrapper.sourceforge.net/mediawiki-1.4.6/index.php/List#B) 
 website say that this card should work. I configured the card in the way explained in the [ubuntu wiki](http://https//wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29). I can modprobe, and get the card up and running as wlan0, but I can't change essid with iwconfig, and it doesn't give a error.
 
 If I scan the network I get 
 sudo iwlist wlan0 scan 
 wlan0 No scan results
 
 I'm trying to connect to a wireless router, SSID Broardcast is on, and I can connect to the network just fin from my Powerbook. I don't use any web-encryption (yet).
 
 KWiFiManager says that the device is connected and the signal is fine but
 Connected to network: any 
 Access point: 00:00:00:00:00:00
 Local IP: unavailable
 
 wlan0 IEEE 802.11g ESSID:off/any
 Mode:Managed Frequency:2.462 GHz Access Point: 00:00:00:00:00:00
 Bit Rate:54 Mb/s Tx-Power:25 dBm
 RTS thr:2347 B Fragment thr:2346 B
 Power Management:off
 Link Quality:100/100 Signal level:-10 dBm Noise level:-256 dBm
 Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
 Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
 - Sune Simonsen

---

### Post by Sune Simonsen on 2005-07-14
Yiiiiha I made this work by changing 
 the line "RadioState|1" to "RadioState|0"
 in /etc/ndiswrapper/bcmwl5a/4E4:4320.conf
 
 - Sune Simonsen

---

