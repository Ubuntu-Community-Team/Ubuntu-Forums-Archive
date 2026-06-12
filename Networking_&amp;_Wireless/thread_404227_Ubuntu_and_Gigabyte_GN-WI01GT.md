---
title: "Ubuntu and Gigabyte GN-WI01GT"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by janek87 on 2007-04-08
hy!.
first i tell, that im not good in english ...
But heres my problem:
I have a laptop with Gigabyte GN-WI01GT wireless card, and its not working in Ubuntu,i use Ubuntu 6.10. Even the Wifi light is not on...i have used ndiswrapper to set drivers and in network is wireless connection on, but not confed. I cant see no wireless connections, and i think that my  card just dont work with Ubuntu :( 
any help?

> janek@janek-laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-94 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by r00tintheb0x on 2007-04-08
I believe you're going to have to madwifi it. :(

---

### Post by janek87 on 2007-04-08
how?
please tell me it very simple, beacause im new one in linux...

---

### Post by r00tintheb0x on 2007-04-08
What do you get from the console output "dmesg |grep ath0" ?

---

### Post by janek87 on 2007-04-08
from dmesg |grep ath0 i dont get nothing, but from dmesg |grep wlan0 i get :

janek@janek-laptop:~$ dmesg |grep wlan0
[17179595.408000] wlan0: vendor: ''
[17179595.408000] wlan0: ethernet device 00:16:e6:30:9c:4e using serialized NDIS driver net5211, 168C:001C.5.conf
[17179595.408000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179606.328000] wlan0: no IPv6 routers present

---

### Post by janek87 on 2007-04-08
is there any hope, that the card is working fine?

---

### Post by Chafnan on 2007-04-21
This card is working for me off the Live CD and install for Ubuntu 7.04.  Hope that will help.

---

