---
title: "Wireless Access Point Association Problems"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by tcrroadie on 2007-09-27
I'm having some difficulty with my wireless card associating itself with one of our wireless networks in my workplace.  My laptop equipment is an IBM T23 with a Belkin F5D7010 Version 7 PCMCIA card. 

The network I want to use is BettenCustomers.  I am able to connect and use this network, but my problem is, that sometimes it will take up to 5 minutes to associate itself with my laptop, and other times my laptop will connect immediately.  Once my laptop has associated itself with the access point, I have no problems using the network.  My connection has never been dropped.  I just have a problem establishing a connection.  Some information from my system below. 

Output from iwlist scan
```

kris@T23:~$ sudo iwlist wlan0 scan
Password:
wlan0     Scan completed :
          Cell 01 - Address: 00:40:96:55:DE:AD
                    ESSID:"fix"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:40:96:55:AC:A9
                    ESSID:"fix"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0F:CB:FF:87:3A
                    ESSID:"BettenCustomers"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 04 - Address: 00:0C:41:D8:41:8F
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

Ndiswrapper driver information.
```

kris@T23:~$ ndiswrapper -l
net8185 : driver installed
        device (1799:701F) present
```

Output from iwconfig.  Here I am connected and using the network BettenCustomers.
```
kris@T23:~$ iwconfig 
lo        no wireless extensions.

eth1      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BettenCustomers"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0F:CB:FF:87:3A   
          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2432 B   Fragment thr=2432 B   
          Power Management:off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

iwpriv shows these additional options available for my wireless card. 
```

kris@T23:~$ iwpriv wlan0 
wlan0     Available private ioctls :
          ndis_reset       (8BF0) : set   0       & get   0      
          power_profile    (8BF1) : set   1 int   & get   0      
          network_type     (8BF2) : set   1 char  & get   0      
          usb_reset        (8BF3) : set   0       & get   0      
          media_stream     (8BF4) : set   1 int   & get   0      
          set_encr_mode    (8BF5) : set   1 int   & get   0      
          set_auth_mode    (8BF6) : set   1 int   & get   0      
          reload_defaults  (8BF7) : set   0       & get   0 
```

My current /etc/network/interfaces file. 
```

# The loopback network interface
auto lo
iface lo inet loopback

# Wired Work Connection
#auto eth1
#iface eth1 inet dhcp

# Wireless Work Network
auto wlan0
iface wlan0 inet static
address 192.168.1.115
netmask 255.255.255.0
gateway 192.168.1.1
pre-up iwpriv wlan0 network_type g
#pre-up iwconfig wlan0 channel 2
#pre-up iwconfig wlan0 essid BettenCustomers
#pre-up iwconfig wlan0 key 6e117704dcd8ee17a47fb78d6d26943214ebcce86e000ac1a06bd446779935ab
wpa-driver wext
wpa-ssid BettenCustomers
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 6e117704dcd8ee17a47fb78d6d26943214ebcce86e000ac1a06bd446779935ab

```

None of my pre-up lines have seem to have made a difference, so I have commented most of them out for now.  

Output from iwevent when my wireless card was trying to establish a connection with repeated failure.
```

kris@T23:~$ sudo iwevent 
Waiting for Wireless Events from interfaces...
11:43:16.670142   wlan0    Set Mode:Managed
11:43:16.670255   wlan0    Set Frequency:2.417 GHz (Channel 2)
11:43:16.670340   wlan0    Set ESSID:"BettenCustomers"
11:43:16.907163   wlan0    Association Request 
IEs:000F42657474656E437573746F6D657273010C82848B968C9298A4B0C8E0ECDD180050F20101000050F20201000050F20201000050F2020000
11:43:16.907262   wlan0    Association Response IEs:010882848B0C12961824
11:43:16.907430   wlan0    New Access Point/Cell address:00:0F:CB:FF:87:3A
11:43:21.419169   wlan0    New Access Point/Cell address:Not-Associated
11:43:27.345848   wlan0    Association Request 
IEs:000F42657474656E437573746F6D657273010C82848B968C9298A4B0C8E0ECDD180050F20101000050F20201000050F20201000050F2020000
11:43:27.345961   wlan0    Association Response IEs:010882848B0C12961824
11:43:27.346177   wlan0    New Access Point/Cell address:00:0F:CB:FF:87:3A
11:43:29.676538   wlan0    Set Mode:Managed
11:43:29.676585   wlan0    Set Frequency:2.417 GHz (Channel 2)
11:43:29.676634   wlan0    Set ESSID:"BettenCustomers"
11:43:31.419776   wlan0    New Access Point/Cell address:Not-Associated
11:43:42.695231   wlan0    Set Mode:Managed
11:43:42.695279   wlan0    Set Frequency:2.417 GHz (Channel 2)
11:43:42.695672   wlan0    Set ESSID:"BettenCustomers"
11:43:42.910633   wlan0    Association Request 
IEs:000F42657474656E437573746F6D657273010C82848B968C9298A4B0C8E0ECDD180050F20101000050F20201000050F20201000050F2020000
11:43:42.910747   wlan0    Association Response IEs:010882848B0C12961824
11:43:42.910955   wlan0    New Access Point/Cell address:00:0F:CB:FF:87:3A
11:43:47.420776   wlan0    New Access Point/Cell address:Not-Associated
```

Output from iweven when my wireless card connected immediately. 

```
kris@T23:~$ iwevent 
Waiting for Wireless Events from interfaces...
15:07:03.268990   wlan0    Set Mode:Managed
15:07:03.478186   wlan0    Set Mode:Managed
15:07:03.478511   wlan0    Set Frequency:2.417 GHz (Channel 2)
15:07:03.478853   wlan0    Set ESSID:"BettenCustomers"
15:07:03.657778   wlan0    Association Request IEs:000F42657474656E437573746F6D657273010C82848B968C9298A4B0C8E0ECDD180050F201
01000050F20201000050F20201000050F2020000
15:07:03.657916   wlan0    Association Response IEs:010882848B0C12961824
15:07:03.658480   wlan0    New Access Point/Cell address:00:0F:CB:FF:87:3A
```

Maybe I am just at the hands of the radio interference gods, but since my wirelesss connection never drops, I am thinking maybe there is something else I am missing.  Any information on this would be greatly appriciated.

---

