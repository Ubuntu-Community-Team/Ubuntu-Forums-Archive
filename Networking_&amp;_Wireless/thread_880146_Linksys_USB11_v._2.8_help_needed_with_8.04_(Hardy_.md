---
title: "Linksys USB11 v. 2.8 help needed with 8.04 (Hardy Heron)"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by Tripp_mongo on 2008-08-04
I have a Linksys USB11 v2.8 wireless adapter that I am trying to get to work with 8.04.  If I boot Ubuntu with the adapter attached, then it usually will not work at all, but it did once.  If I attach it after the X server has loaded and enable wireless, then it will give me a list of wireless access points in the area.  It has only connected twice, and once it actually allowed me to access yahoo, but then it stopped the transmission thereafter. 

When the device is attached, then I start having delays and overruns with my keyboard inputs. 

It differs from the v2.6 in that the v2.8 has an atmel chip set.  

Here are the readings from lsusb and iwconfig.  As you can see I tried to connect to two different acces points.  I even tried to connect by removing the MAC filters and all security from the access points, but still no luck.  

Does anyone have any ideas as to what is going on here?  It use to work with the older linux kernel.  

___________________________________________________________________

hal@hal-desktop:~$ lsusb

Bus 005 Device 002: ID 04b8:0839 Seiko Epson Corp. 

Bus 005 Device 001: ID 0000:0000  

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 004: ID 1915:2233   [B]<--------- (This is the device, but 
there is no info about it here)[/B]
Bus 001 Device 001: ID 0000:0000  

hal@hal-desktop:~$ 

hal@hal-desktop:~$ 

hal@hal-desktop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11b  ESSID:off/any  Nickname:""

          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   

          Bit Rate:11 Mb/s   Tx-Power=15 dBm   

          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



hal@hal-desktop:~$ 

hal@hal-desktop:~$ 

hal@hal-desktop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11b  ESSID:"belkin54g"  Nickname:""

          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   

          Bit Rate:11 Mb/s   Tx-Power=15 dBm   

          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   

          Power Management:off

          Link Quality:96/100  Signal level:100/100  

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



hal@hal-desktop:~$ 

hal@hal-desktop:~$ 

hal@hal-desktop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11b  ESSID:"dlink1"  Nickname:""

          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   

          Bit Rate:11 Mb/s   Tx-Power=15 dBm   

          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



hal@hal-desktop:~$ 

_________________________________________________________

Again, any help would be much appreciated.

---

### Post by Tripp_mongo on 2008-08-07
Doesn't anyone have an idea?

---

