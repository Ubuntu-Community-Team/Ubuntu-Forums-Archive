---
title: "Belkin N150 Wireless USB Adaptor: WiFi connection regularly drops [Realtek RTL8188SU]"
date: 2015-04-24
forum: Networking &amp; Wireless
---

### Post by petervanbruystegem on 2015-04-24
This is extremely annoying and keeps me from using/enjoying my Ubuntu based Linux OS :-/

 My WiFi connection regularly drops and reconnects all by itself. Sometimes it keeps connecting for ages!
Other times it still keeps connected but no packets can be send/received?!
When connection does work, it slows down after a while and I never reach the full potential of the Wireless adaptor...
I then run **sudo restart network-manager**, which sometimes works and sometimes not at all :/

Can someone with knowledge please advice/help me with this?
I'm running elementary OS 0.3 Freya, built on Ubuntu 14.04 and using the **Belkin N150** (F7D1101 v1) basic Wireless USB Adaptor [**Realtek RTL8188SU**]

Many thanks in advance!

Here is my wireless info script output (old version, as the new one gives me a blank output):
 
```

########## wireless info START ##########

Report from: 24 Apr 2015 14:22 CEST +0200

Booted last: 24 Apr 2015 13:47 CEST +0200

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    [COLOR=#008080]**elementary OS**[/COLOR]
Description:       **[COLOR=#008080]elementary OS Freya[/COLOR]**
Release:           **[COLOR=#008080]0.3[/COLOR]**
Codename:          **[COLOR=#008080]freya[/COLOR]**

##### kernel ############################

Linux 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, nouveau.blacklist=1, nomodeset, vt.handoff=7

##### desktop ###########################

Pantheon

##### lspci #############################

##### lsusb #############################

Bus 001 Device 002: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [[COLOR=#000080]**Realtek RTL8188SU**[/COLOR]]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              494362  0 
[COLOR=#ff0000]**r8712u**[/COLOR]                184139  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.114.71.220  Bcast:10.114.71.255  Mask:255.255.252.0
          inet6 addr: fe80::ee1a:59ff:fe4d:f421/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24711 errors:0 **dropped:12014** overruns:0 frame:0
          TX packets:18427 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36236873 (36.2 MB)  TX bytes:1706743 (1.7 MB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TELENETHOMESPOT"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'TELENETHOMESPOT' [AC1]>   
          Bit Rate:65 Mb/s   Sensitivity:0/0  
          Retry:**off**   RTS thr:**off**   Fragment thr:**off**
          Power Management:**off**
          Link Quality=52/100  Signal level=92/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.114.68.1     0.0.0.0         UG    0      0        0 wlan0
10.114.68.0     0.0.0.0         255.255.252.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search telenet.be

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [TELENETHOMESPOT] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            [COLOR=#ff0000]**r8712u**[/COLOR]
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TelenetWiFree:   Infra, <MAC 'TelenetWiFree' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 96 WPA WPA2 Enterprise
    telenet-6CD49:   Infra, <MAC 'telenet-6CD49' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2
    TelenetWiFree:   Infra, <MAC 'TelenetWiFree' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2 Enterprise
    WiFi-2.4-18c8:   Infra, <MAC 'WiFi-2.4-18c8' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92 WPA2
    TelenetWiFree:   Infra, <MAC 'TelenetWiFree' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2 Enterprise
    TelenetWiFree:   Infra, <MAC 'TelenetWiFree' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2 Enterprise
    telenet-C6A27:   Infra, <MAC 'telenet-C6A27' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    telenet-2633D:   Infra, <MAC 'telenet-2633D' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 58 WPA WPA2
    WiFi-2.4-cc3e:   Infra, <MAC 'WiFi-2.4-cc3e' [AC19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    SNOW_Tienen:     Infra, <MAC 'SNOW_Tienen' [AN10]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 47 WPA2
    Snow - l144:     Infra, <MAC 'Snow - l144' [AC12]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 46 WPA WPA2
    PROXIMUS_FON:    Infra, <MAC 'PROXIMUS_FON' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92
    TELENETHOMESPOT: Infra, <MAC 'TELENETHOMESPOT' [AC22]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 58
    PROXIMUS_FON:    Infra, <MAC 'PROXIMUS_FON' [AC20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    TELENETHOMESPOT: Infra, <MAC 'TELENETHOMESPOT' [AC18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 58
    PROXIMUS_FON:    Infra, <MAC 'PROXIMUS_FON' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47
    telenet-F4BF4:   Infra, <MAC 'telenet-F4BF4' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    SHOP_BEL:        Infra, <MAC 'SHOP_BEL' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 58 WPA2
    PROXIMUS_FON:    Infra, <MAC 'PROXIMUS_FON' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44
    HQ_BEL:          Infra, <MAC 'HQ_BEL' [AN20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 58 WPA2
    TELENETHOMESPOT: Infra, <MAC 'TELENETHOMESPOT' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 87
    *TELENETHOMESPOT:Infra, <MAC 'TELENETHOMESPOT' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62
    TelenetWiFree:   Infra, <MAC 'TelenetWiFree' [AC21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 46 WPA WPA2 Enterprise
    TELENETHOMESPOT: Infra, <MAC 'TELENETHOMESPOT' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    WiFi-2.4-64f8:   Infra, <MAC 'WiFi-2.4-64f8' [AN25]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 56 WPA2
    telenet-0E849:   Infra, <MAC 'telenet-0E849' [AN26]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    WiFi-2.4-2EE9:   Infra, <MAC 'WiFi-2.4-2EE9' [AN27]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2

  IPv4 Settings:
    Address:         10.114.71.220
    Prefix:          22 (255.255.252.0)
    Gateway:         10.114.68.1

    DNS:             195.130.130.134
    DNS:             195.130.131.134

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/TELENETHOMESPOT]] (600 root)
[connection] id=TELENETHOMESPOT | type=802-11-wireless
[802-11-wireless] ssid=TELENETHOMESPOT | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/Brussels (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      6   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      10   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TELENETHOMESPOT' [AC1]>
                    ESSID:"TELENETHOMESPOT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=100/100  
          Cell 02 - Address: <MAC 'TELENETHOMESPOT' [AC2]>
                    ESSID:"TELENETHOMESPOT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:**off**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=92/100  
          Cell 03 - Address: <MAC 'TelenetWiFree' [AC3]>
                    ESSID:"TelenetWiFree"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac010000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=92/100  
          Cell 04 - Address: <MAC 'telenet-F4BF4' [AC4]>
                    ESSID:"telenet-F4BF4"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Signal level=92/100  
          Cell 05 - Address: <MAC 'TelenetWiFree' [AC5]>
                    ESSID:"TelenetWiFree"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac010000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=72/100  
          Cell 06 - Address: <MAC 'telenet-6CD49' [AC6]>
                    ESSID:"telenet-6CD49"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Signal level=74/100  
          Cell 07 - Address: <MAC 'WiFi-2.4-18c8' [AC7]>
                    ESSID:"WiFi-2.4-18c8"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=92/100  
          Cell 08 - Address: <MAC 'PROXIMUS_FON' [AC8]>
                    ESSID:"PROXIMUS_FON"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:**off**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=96/100  
          Cell 09 - Address: <MAC 'SHOP_BEL' [AC9]>
                    ESSID:"SHOP_BEL"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=58/100  
          Cell 10 - Address: <MAC 'PROXIMUS_FON' [AC10]>
                    ESSID:"PROXIMUS_FON"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:**off**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=44/100  
          Cell 11 - Address: <MAC 'PROXIMUS_FON' [AC11]>
                    ESSID:"PROXIMUS_FON"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:**off**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=46/100  
          Cell 12 - Address: <MAC 'Snow - l144' [AC12]>
                    ESSID:"Snow - l144"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  
          Cell 13 - Address: <MAC 'telenet-C6A27' [AC13]>
                    ESSID:"telenet-C6A27"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Signal level=56/100  
          Cell 14 - Address: <MAC 'telenet-2633D' [AC14]>
                    ESSID:"telenet-2633D"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Signal level=56/100  
          Cell 15 - Address: <MAC 'TelenetWiFree' [AC15]>
                    ESSID:"TelenetWiFree"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac010000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=56/100  
          Cell 16 - Address: <MAC 'TelenetWiFree' [AC16]>
                    ESSID:"TelenetWiFree"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac010000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=47/100  
          Cell 17 - Address: <MAC 'TELENETHOMESPOT' [AC17]>
                    ESSID:"TELENETHOMESPOT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:**off**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=56/100  
          Cell 18 - Address: <MAC 'TELENETHOMESPOT' [AC18]>
                    ESSID:"TELENETHOMESPOT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:**off**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=62/100  
          Cell 19 - Address: <MAC 'WiFi-2.4-cc3e' [AC19]>
                    ESSID:"WiFi-2.4-cc3e"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

7656D436F6D10230017536167656D636F6D4661737433383635625F42424F583310240009532E322E302D312E301042000F4C4B313431303344503336303031361054000800060050F20400011011001C536167656D636F6D4661737433383635625F42424F58332D4C4B313410080002200C103C0001011049000600372A000120
                    Signal level=44/100  
          Cell 20 - Address: <MAC 'PROXIMUS_FON' [AC20]>
                    ESSID:"PROXIMUS_FON"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:**off**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=44/100  
          Cell 21 - Address: <MAC 'TelenetWiFree' [AC21]>
                    ESSID:"TelenetWiFree"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac010000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=56/100  
          Cell 22 - Address: <MAC 'TELENETHOMESPOT' [AC22]>
                    ESSID:"TELENETHOMESPOT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:**off**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=60/100  

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_**disable**_40mhz_24ghz:**Disable** 40MHz support in the 2.4GHz band (bool)

[**[COLOR=#ff0000]r8712u[/COLOR]**]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/staging/rtl8712/[COLOR=#ff0000]**r8712u.ko**[/COLOR]
firmware:       rtlwifi/**[COLOR=#ff0000]rtl8712u.bin[/COLOR]**
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     9A0BDB5A266844AB0999460
depends:        
staging:        Y
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

##### module parameters #################

[cfg80211]
cfg80211_**disable**_40mhz_24ghz: N
ieee80211_regdom: 00

[[COLOR=#ff0000]**r8712u**[/COLOR]]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x ([COLOR=#ff0000]**r8712u**[/COLOR])
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   14.283253] r8712u: Staging version
[   14.283296] r8712u: register rtl8712_netdev_ops to netdev_ops
[   14.283302] usb 1-5: r8712u: USB_SPEED_HIGH with 4 endpoints
[   14.292084] usb 1-5: r8712u: Boot from EFUSE: Autoload OK
[   16.081327] usb 1-5: r8712u: CustomerID = 0x0000
[   16.081334] usb 1-5: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[   16.081337] usb 1-5: r8712u: Loading firmware from "rtlwifi/**[COLOR=#ff0000]rtl8712u.bin[/COLOR]**"
[   18.324074] r8712u 1-5:1.0 wlan0: 1 RCR=0x153f00e
[   18.326143] r8712u 1-5:1.0 wlan0: 2 RCR=0x553f00e
[   18.453131] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (**repeated 2 times**)
[   39.601007] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############

```

---

### Post by petervanbruystegem on 2015-04-24
It's weird why there is no **lspci** and **rfkill** output in the above script!?
Is there a way to do this manually, so I can provide some more information?

Many thanks!

---

### Post by kurt18947 on 2015-04-24
It appears that many Realtek devices are driven by the same driver. If I go to Realtek's site and search for wireless drivers, I find a list of RTL8188xx and RTL8192xx devices using the same driver. Among them are RTL8188SU and RTL8192CU. 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

The drivers from Realtek won't install on Ubuntu versions newer than 12.10.  There is a patched version that works with my 8192cu and 8188cus devices on current releases. If it were me, I'd download this, install it and see if it helps.

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

I just go to the above site using an account with sudo privileges, open a terminal and copy/paste one line at a time then reboot. If this is a bad idea, I hope someone will come along and say so.

---

### Post by petervanbruystegem on 2015-04-24
> **kurt18947 said:**
> It appears that many Realtek devices are driven by the same driver...

Thank you for your response and suggestion!

I went to the site, looked at it and did the following:

1. I left out "linux-headers-generic", otherwise it would have downgrade my 3.16.x kernel to 3.13.x (I don't want that)
2. I left out "dkms" because that was already installed on my system
3. I added "git", because that was not yet installed on my system

So, I came out with this:

```
sudo apt-get install build-essential git
sudo reboot
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
```


Of course, that went fine... But, I'm not sure about the next steps:

- Set it up as a DKMS module
- Build and install it
- Refresh the module list
- [B]Ensure the native (and broken) kernel driver is blacklisted
[/B]
This because I don&#8217;t have the "native-rtl8192.conf" mentioned on that site but using this (see wireless info script output):

[I]filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin[/I]


Also, it would be nice to know how to revert back to the above native driver in case the fixed one doesn't work ;-)

As I have very little knowledge on this, it would be a great help if you (or someone else) could tell me how to this.
I would tike to give this fixed driver a try...

---

### Post by kurt18947 on 2015-04-25
I'm afraid I'm not of much help with your questions. I have swapped back and forth between the broken and patched modules. The original broken module is rtl8192cu. The patched module shows as 8192cu, no rtl in front. I just blacklist the one I don't want to load. That seems to work. 

r8712 is I believe another Realtek module. I have a Trendnet TEW-649UB (I think) USB wifi adapter containing an rtl8192**SU** chip that loads that module. It works very well using the native driver, no patched or alternative driver required.

---

