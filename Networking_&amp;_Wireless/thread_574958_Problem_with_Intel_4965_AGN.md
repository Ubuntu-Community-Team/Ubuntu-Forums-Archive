---
title: "Problem with Intel 4965 AGN"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by odrium on 2007-10-13
Greetings. I have a sony vaio with a Intel 4965 WiFi card. I installed the card with ndiswrapper using [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty"). 

And after that I "enabled" wpa security using [this guide]("http://ubuntuforums.org/showthread.php?t=202834").

I tried to enter to my network and the connection dropped almost 5 second after it connected and then it connected, and dropped ........

So when I restarted the computer I couldn't see my wireless adapter in the Network Manager. And I can see it with iwconfig so I know is working but I can't connect to WPA. Please help!!!!

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=150 Mb/s   
          Fragment thr=1500000 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.


$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid Belkin
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk c1d7e987febe9e51153e4d4d1217a03177e9c5e4cf632723497d21963341b0ab

---

