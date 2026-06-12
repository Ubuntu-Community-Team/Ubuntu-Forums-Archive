---
title: "Feisty Cisco Airo-340 Config?"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by Barkingdoggy on 2007-08-25
Feisty recognizes the PCMCIA card, sees the wireless network, but I cannot associate with an access point.  I followed the steps in [http://ubuntuforums.org/showthread.php?t=255704](http://ubuntuforums.org/showthread.php?t=255704) without luck.  My machine is dual boot, and the card works fine in Windows.  

TIA for any assistance...
Barkingdoggy

FYI:
$ cat /proc/driver/aironet/eth1/Status
Status: CFG ACT SYN LNK 
Mode: 3f
Signal Strength: 93
Signal Quality: 4
SSID: Wireless
AP: 
Freq: 0
BitRate: 11mbs
Driver Version: airo.c 0.6 (Ben Reed & Javier Achirica)
Device: 340 Series
Manufacturer: Cisco Systems
Firmware Version: 4.25.30
Radio type: 2
Country: 0
Hardware Version: 11
Software Version: 425
Software Subversion: 1e
Boot block version: 143

$ cat /proc/driver/aironet/eth1/Config
Mode: ESS
Radio: on
NodeName:                 
PowerMode: CAM
DataRates: 2 4 11 22 0 0 0 0
Channel: 6
XmitPower: 30
LongRetryLimit: 16
ShortRetryLimit: 16
RTSThreshold: 2312
TXMSDULifetime: 5000
RXMSDULifetime: 10000
TXDiversity: both
RXDiversity: both
FragThreshold: 2312
WEP: open
Modulation: cck
Preamble: short

---

### Post by Darkhack on 2007-08-25
Try turning off all security features (enable SSID broadcasting, disable WEP/WPA) and see if you can connect to it.  Could you also post the output of "iwconfig" and "less /etc/network/interfaces"?

---

### Post by Barkingdoggy on 2007-08-26
DarkHack - Thanks for your reply.  This is an open network - no encryption.  SSID is broadcast by the AP.  - Barkingdoggy

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11-DS  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:30:AB:22:AE:E8   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-47 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:45   Missed beacon:0
wifi0     IEEE 802.11-DS  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:30:AB:22:AE:E8   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-47 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:45   Missed beacon:0

less /etc/network/interfaces:
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
iface wlan0 inet dhcp
wireless-essid Wireless
auto wlan0
iface eth1 inet dhcp
wireless-essid Wireless
auto eth1

%%%%%%%%%

---

