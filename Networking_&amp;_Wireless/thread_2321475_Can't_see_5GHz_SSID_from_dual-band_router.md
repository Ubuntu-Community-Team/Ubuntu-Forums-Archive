---
title: "Can't see 5GHz SSID from dual-band router"
date: 2016-04-22
forum: Networking &amp; Wireless
---

### Post by DM2016 on 2016-04-22
Hi, all help very gratefully received :)

I have an Asus RT-N66U dual-band router.  My linux laptop cannot see the 5GHz SSID, but it can see and connect to the 2.4GHz SSID.  My Android phone can see and connect to the 5GHz SSID no problems.  

I've searched for solutions with no luck.  Here is some info that might be useful for those willing to help: 

$ iwconfig
wlan0     IEEE 802.11abg  ESSID:"SKYA9999"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 7C:4C:A5:FD:06:D5   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

$ lspci -nn -d 14e4:
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)


$ iwlist wlan0 freq
wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Current Frequency:2.412 GHz (Channel 1)

---

### Post by DM2016 on 2016-04-23
This might be related: 
My laptop is constantly dropping connection - it's definitely the laptop and not other devices.  This connection is sometimes able to be reset by disconnecting manually from the network and reconnecting, but sometimes the laptop has to be rebooted.  
I running 14.04.  
The laptop is no longer appearing on the router's client list, even at times when it is clearly connected.  

This is doing my head in and any help will be much appreciated.  Thanks

---

### Post by weatherman2 on 2016-04-23
Read the "sticky" post at the top of this forum and run the "wireless info script" described above, then post the results here in your thread.

---

