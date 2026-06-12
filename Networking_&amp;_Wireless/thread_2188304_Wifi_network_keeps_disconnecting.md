---
title: "Wifi network keeps disconnecting"
date: 2013-11-16
forum: Networking &amp; Wireless
---

### Post by luisvalladares94 on 2013-11-16
Hello.

I've a wifi network on my house, my route is a TP-Link TL-WR741ND and the ethernet controller of my computer is a Qualcomm Atheros AR5212/AR5213 Wireless Network Adapter (rev 01). i've a random issue, i mean, dont happen every time, but is frequently (twice a day at least). 

My wifi sometimes enter on a disconnect loop, i mean, the system say the networks has been disconnected, try to reconnect again, connect for a second and disconnect again, sometimes prompt a window to type the Key to enter, other times the WiFi network disappear from the list and i've to disable and enable the wireless connection, stay with this problem for about 30 to 90 minutes and after that the network start working perfectly, without touching anything.

I'm using now Ubuntu 13.10 but in 13.04 happens too, the other wifi devices dont disconnect so i assume its not a problem of the router, also i try to connect using winbug 7 in the same computer and the connection is strong.

Here is some data, any other info you need just let me know

```
sudo iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"C139F47MD3NB"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 64:66:B3:A6:43:7A   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:349  Invalid misc:180   Missed beacon:0

```

---

