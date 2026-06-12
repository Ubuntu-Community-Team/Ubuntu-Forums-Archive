---
title: "Network Manager and Static ip. and stuff"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by Marsjannno on 2007-04-28
Hi,

I have installed ubuntu this week. I have got a problem with Wireless network.
Ubuntu properly recognised my wifi card (Atheros), then i set up all data neded (static ip, gateway, dns's etc.) after that I restarted Network interface, but network connection didn't start. It doesen't work. How can i work it out?

My:
iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"dom"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/94  Signal level=-79 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist:
```
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event 
```
ifconfig:
```

Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event 

```
and:
```
#auto lo
#iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet static
address 192.168.20.2
netmask 255.255.255.0
gateway 192.168.20.252
wireless-essid dom
wireless-key 7894561230

#auto wlan0
#iface wlan0 inet dhcp
```

---

