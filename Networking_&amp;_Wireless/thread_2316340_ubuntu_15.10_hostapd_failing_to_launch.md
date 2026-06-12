---
title: "ubuntu 15.10 hostapd failing to launch"
date: 2016-03-07
forum: Networking &amp; Wireless
---

### Post by r_al_sim on 2016-03-07
hi anyone got any ideas for me to try other than building hostapd from trunk

trying to set up a wireless usb to work as an access point

when i try to launch hostapd i get the following

sudo hostapd /etc/hostapd.conf
Configuration file: /etc/hostapd.conf
nl80211: Driver does not support authentication/association or connect commands
nl80211 driver initialization failed.
hostapd_free_hapd_data: Interface ra0 wasn't started

i've googled but keep coming accross raspberry pie people  saying they changed the version of hostapd to a later build 2.5 but from what i can see it only goes up to 2.4 so a little confused current version in ubuntu 15 is 2.1 

hostapd has minimal config

interface=ra0
driver=nl80211
ssid=test
channel=6


so you can see what card it is
lsusb

Bus 001 Device 003: ID 148f:7601 Ralink Technology, Corp. 


lshw

  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: ac:a2:13:12:04:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN ip=10.1.2.1 multicast=yes wireless=Ralink STA



ethtool -i ra0 | grep driver
driver: RALINK WLAN

sudo iwconfig ra0
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"MT7601STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

