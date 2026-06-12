---
title: "PCI WiFi card could not connect to AP"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by errhec on 2007-02-07
Hi
I have trouble to get the WiFi card connect to the AP.
I try to ifdown and ifup install the WiFi-radar and only once was able to make the connection for 15 minutes  then connection fall of and i'm stuck.
I tray to scan the net iwlist wlan0 scanning and only once ( when worked ) it was scan ok.
Since then I get the scan without result.
I run XP on same machine and WiFi goes OK .
Is reason not enough strong signal?
How can detect other cards ( PCMCIA from my LAPTOP)
Here is the C/P from terminal
Thank you for any help

errhec@errhec:~$ sudo iwconfig
Password:
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"errhec"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:off
          Power Management:off
          Link Quality=34/100  Signal level=8/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

errhec@errhec:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0E:2E:34:8D:40
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality=34/100  Signal level=8/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s

errhec@errhec:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:40:f4:c3:9e:f7
Sending on   LPF/wlan0/00:40:f4:c3:9e:f7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
errhec@errhec:~$ ping -c 4 192.168.0.1
connect: Network is unreachable
errhec@errhec:~$


NOW WHEN SCAN I ONLY GET THIS


errhec@errhec:~$sudo iwlist wlan0 scanning
wlan0 No scan results
errhec@errhec:~$ iwconfig
lo no wireless extensions.

---

