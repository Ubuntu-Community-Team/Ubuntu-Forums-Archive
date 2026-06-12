---
title: "Airmon-ng MONITOR MODE NOT SUPPORTED"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by kaits6610 on 2011-01-15
I need help!

How to fix that problem?! What is wrong with my networck card?

root@ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"WLAN"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:1F:1F:2B:78:70   
          Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=83/100  Signal level:-81 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11abg  ESSID:"WLAN"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: DE:C2:46:62:B0:79   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@ubuntu:~# airmon-ng


Interface    Chipset        Driver

/usr/sbin/airmon-ng: line 174: [: too many arguments
/usr/sbin/airmon-ng: line 179: [: too many arguments
/usr/sbin/airmon-ng: line 184: [: too many arguments
/usr/sbin/airmon-ng: line 189: [: too many arguments
/usr/sbin/airmon-ng: line 194: [: too many arguments
/usr/sbin/airmon-ng: line 199: [: too many arguments
/usr/sbin/airmon-ng: line 204: [: too many arguments
/usr/sbin/airmon-ng: line 209: [: too many arguments
/usr/sbin/airmon-ng: line 214: [: too many arguments
/usr/sbin/airmon-ng: line 219: [: too many arguments
/usr/sbin/airmon-ng: line 224: [: too many arguments
/usr/sbin/airmon-ng: line 229: [: too many arguments
/usr/sbin/airmon-ng: line 234: [: too many arguments
/usr/sbin/airmon-ng: line 239: [: too many arguments
/usr/sbin/airmon-ng: line 244: [: too many arguments
/usr/sbin/airmon-ng: line 249: [: too many arguments
/usr/sbin/airmon-ng: line 254: [: too many arguments
/usr/sbin/airmon-ng: line 259: [: too many arguments
/usr/sbin/airmon-ng: line 264: [: too many arguments
/usr/sbin/airmon-ng: line 269: [: too many arguments
/usr/sbin/airmon-ng: line 274: [: too many arguments
/usr/sbin/airmon-ng: line 279: [: too many arguments
/usr/sbin/airmon-ng: line 538: [: too many arguments
/usr/sbin/airmon-ng: line 567: [: too many arguments
/usr/sbin/airmon-ng: line 585: [: too many arguments
/usr/sbin/airmon-ng: line 585: [: too many arguments
/usr/sbin/airmon-ng: line 600: [: too many arguments
/usr/sbin/airmon-ng: line 629: [: too many arguments
/usr/sbin/airmon-ng: line 641: [: too many arguments
/usr/sbin/airmon-ng: line 701: [: too many arguments
/usr/sbin/airmon-ng: line 727: [: too many arguments
/usr/sbin/airmon-ng: line 753: [: too many arguments
/usr/sbin/airmon-ng: line 815: [: too many arguments
/usr/sbin/airmon-ng: line 842: [: too many arguments
/usr/sbin/airmon-ng: line 869: [: too many arguments
/usr/sbin/airmon-ng: line 888: [: too many arguments
/usr/sbin/airmon-ng: line 915: [: too many arguments
/usr/sbin/airmon-ng: line 944: [: too many arguments
/usr/sbin/airmon-ng: line 973: [: too many arguments
/usr/sbin/airmon-ng: line 991: [: too many arguments
/usr/sbin/airmon-ng: line 1009: [: too many arguments
/usr/sbin/airmon-ng: line 1028: [: too many arguments
/usr/sbin/airmon-ng: line 1047: [: too many arguments
/usr/sbin/airmon-ng: line 1064: [: too many arguments
/usr/sbin/airmon-ng: line 1081: [: too many arguments
/usr/sbin/airmon-ng: line 1097: [: too many arguments
wlan0        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)
Ralink        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)
STA        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)
ESSID:"WLAN"        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)
Nickname:"RT2870STA"        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)
/usr/sbin/airmon-ng: line 174: [: too many arguments
/usr/sbin/airmon-ng: line 179: [: too many arguments
/usr/sbin/airmon-ng: line 184: [: too many arguments
/usr/sbin/airmon-ng: line 189: [: too many arguments
/usr/sbin/airmon-ng: line 194: [: too many arguments
/usr/sbin/airmon-ng: line 199: [: too many arguments
/usr/sbin/airmon-ng: line 204: [: too many arguments
/usr/sbin/airmon-ng: line 209: [: too many arguments
/usr/sbin/airmon-ng: line 214: [: too many arguments
/usr/sbin/airmon-ng: line 219: [: too many arguments
/usr/sbin/airmon-ng: line 224: [: too many arguments
/usr/sbin/airmon-ng: line 229: [: too many arguments
/usr/sbin/airmon-ng: line 234: [: too many arguments
/usr/sbin/airmon-ng: line 239: [: too many arguments
/usr/sbin/airmon-ng: line 244: [: too many arguments
/usr/sbin/airmon-ng: line 249: [: too many arguments
/usr/sbin/airmon-ng: line 254: [: too many arguments
/usr/sbin/airmon-ng: line 259: [: too many arguments
/usr/sbin/airmon-ng: line 264: [: too many arguments
/usr/sbin/airmon-ng: line 269: [: too many arguments
/usr/sbin/airmon-ng: line 274: [: too many arguments
/usr/sbin/airmon-ng: line 279: [: too many arguments
wlan1        Unknown     lrwxrwxrwx 1 root root 0 2011-01-15 08:03 /sys/class/net/wlan1/device/driver -> ../../../../bus/pci/drivers/iwl3945 - [lrwxrwxrwx 1 root root 0 2011-01-15 08:03 /sys/class/net/wlan1/phy80211 -> ../../ieee80211/phy0]
IEEE        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)
802.11abg        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)
ESSID:"WLAN"        Unknown        Unknown (MONITOR MODE NOT SUPPORTED)

root@ubuntu:~#

---

