---
title: "Wi-Fi stops working when power unplugged. 14.04 LTS, Dell XPS 18, Intel Wireless 7260"
date: 2015-01-05
forum: Networking &amp; Wireless
---

### Post by evgeniy4 on 2015-01-05
[SIZE=2][FONT=arial][COLOR=#333333]It works like a charm when plugged in and can not connect to any network when unplugged. Have no problems when using Windows.[/COLOR]
[COLOR=#333333]I did all upgrades and even upgraded the kernel to 3.18. I've tried the solutions below :[/COLOR]
[/FONT][/SIZE]
[LIST=1]
[*][SIZE=2][FONT=arial]Add "options iwlwifi 11n_disabled=1" in /etc/modprobe.d/iwlwifi.conf[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Ignore IPv6[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Restart NetworkManager[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Switch off power management[/FONT][/SIZE]
[/LIST]
[SIZE=2][FONT=arial][COLOR=#333333]None of them solved the problem.[/COLOR]
[COLOR=#333333]From dmesg I see the folowing when it crashed :
[/COLOR]
```
iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5

```

[COLOR=#333333]Here is the complet infromation from wireless script :
[/COLOR]```


########## wireless info START ##########


Report from: 05 Jan 2015 22:26 CET +0100


Booted last: 05 Jan 2015 22:22 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.18.1-031801-generic #201412170637 SMP Wed Dec 17 11:38:50 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c470]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 8087:07dc Intel Corp. 
Bus 001 Device 005: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 0457:1039 Silicon Integrated Systems Corp. 
Bus 001 Device 002: ID 0c45:6621 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


snd_soc_rt5640         93325  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          207780  1 snd_soc_rt5640
dell_wmi_aio           12652  0 
sparse_keymap          13890  1 dell_wmi_aio
iwlmvm                254598  0 
mac80211              697159  1 iwlmvm
iwlwifi               193813  1 iwlmvm
snd_pcm               106273  6 snd_soc_rt5640,snd_soc_core,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
cfg80211              520257  3 iwlwifi,mac80211,iwlmvm
wmi                    19379  1 dell_wmi_aio


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2ab2:bdff:fea1:207a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13379303 (13.3 MB)  TX bytes:693541 (693.5 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"pysch42"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'pysch42' [AC1]>   
          Bit Rate=36 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:60   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [pysch42] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           12 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    sushe305:        Infra, <MAC 'sushe305' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    Connectify-Unal: Infra, <MAC 'Connectify-Unal' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WPA2
    Loading ...:     Infra, <MAC 'Loading ...' [AN3]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    TP-LINK_06F0:    Infra, <MAC 'TP-LINK_06F0' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    Soleil:          Infra, <MAC 'Soleil' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 65 WPA2
    Shabb Mac :      Infra, <MAC 'Shabb Mac ' [AC10]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 49 WPA2
    eduroam:         Infra, <MAC 'eduroam' [AN7]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2 Enterprise
    Good luck:       Infra, <MAC 'Good luck' [AN8]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    tougariss:       Ad-Hoc, <MAC 'tougariss' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 65 WEP
    Invites-Telecom: Infra, <MAC 'Invites-Telecom' [AN10]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 24
    *pysch42:        Infra, <MAC 'pysch42' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
    SEN:             Infra, <MAC 'SEN' [AN12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Cisco46776:      Infra, <MAC 'Cisco46776' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Connectify-qmip: Infra, <MAC 'Connectify-qmip' [AC24]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    khayri:          Ad-Hoc, <MAC 'khayri' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    eduroam:         Infra, <MAC 'eduroam' [AN16]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2 Enterprise
    Connexion_Beta:  Infra, <MAC 'Connexion_Beta' [AC4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    juliant:         Infra, <MAC 'juliant' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA
    Rezel-Admin:     Infra, <MAC 'Rezel-Admin' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Tardis:          Infra, <MAC 'Tardis' [AC9]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 37 WPA2
    ANDREI_Network:  Infra, <MAC 'ANDREI_Network' [AC6]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 69 WEP
    cocktail-party:  Infra, <MAC 'cocktail-party' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA2
    Rezel:           Infra, <MAC 'Rezel' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    Connectify-Taps: Infra, <MAC 'Connectify-Taps' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    Telecom-ParisTech: Infra, <MAC 'Telecom-ParisTech' [AC5]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2 Enterprise
    Telecom-ParisTech: Infra, <MAC 'Telecom-ParisTech' [AC15]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2 Enterprise


  IPv4 Settings:
    Address:         192.168.1.122
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             137.194.15.218
    DNS:             137.194.15.200


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


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/pysch42]] (600 root)
[connection] id=pysch42 | type=802-11-wireless
[802-11-wireless] ssid=pysch42 | mac-address=<MAC 'wlan0' [IF]> | mtu=1500
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Connectify-Unal]] (600 root)
[connection] id=Connectify-Unal | type=802-11-wireless
[802-11-wireless] ssid=Connectify-Unal | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)


country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


lo        no frequency information.


wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      4   APs on   Frequency:2.457 GHz (Channel 10)
      6   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.2 GHz (Channel 40)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'pysch42' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"pysch42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000cd7db935794
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'cocktail-party' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"cocktail-party"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000527524a19b
                    Extra: Last beacon: 17688ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Cisco46776' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Cisco46776"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000179669ba75
                    Extra: Last beacon: 14184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Connexion_Beta' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Connexion_Beta"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000048045cbdf59
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Telecom-ParisTech' [AC5]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Telecom-ParisTech"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001ed3b82d698e
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'ANDREI_Network' [AC6]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"ANDREI_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ca85639156
                    Extra: Last beacon: 17572ms ago
          Cell 07 - Address: <MAC 'TP-LINK_06F0' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_06F0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000455b711a823
                    Extra: Last beacon: 14184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'sushe305' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"sushe305"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000050ba99ac19
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Tardis' [AC9]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Tardis"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000003436b2cf
                    Extra: Last beacon: 14184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Shabb Mac ' [AC10]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Shabb Mac "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001f9d84ae1
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC '\00\00\00\00\00' [AC11]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000177a5a1bf
                    Extra: Last beacon: 17400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Connectify-Unal' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Connectify-Unal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000326b55fa1
                    Extra: Last beacon: 3176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Rezel' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Rezel"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000051e0a82180
                    Extra: Last beacon: 17344ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC 'juliant' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"juliant"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002b636ebcf08
                    Extra: Last beacon: 17344ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'Telecom-ParisTech' [AC15]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Telecom-ParisTech"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006732f67d81
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 16 - Address: <MAC 'Rezel-Admin' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Rezel-Admin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000051e0a8f046
                    Extra: Last beacon: 17344ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'Connectify-Taps' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Connectify-Taps"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f2f99885
                    Extra: Last beacon: 17344ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'Aymen Wifi' [AC18]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Aymen Wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d2bf6119
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'Invites-Telecom' [AC19]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"Invites-Telecom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001ed3b82e6e78
                    Extra: Last beacon: 52ms ago
          Cell 20 - Address: <MAC 'eduroam' [AC20]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001ed3b82d0695
                    Extra: Last beacon: 3408ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 21 - Address: <MAC 'JVN605' [AC21]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"JVN605"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a9621fc05
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'Invites-Telecom' [AC22]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"Invites-Telecom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006732f8a363
                    Extra: Last beacon: 3216ms ago
          Cell 23 - Address: <MAC 'eduroam' [AC23]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006732f709c1
                    Extra: Last beacon: 3200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 24 - Address: <MAC 'Connectify-qmip' [AC24]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Connectify-qmip"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000031b5f95
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


2C01C800140005001900
          Cell 25 - Address: <MAC 'Telecom-ParisTech' [AC25]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Telecom-ParisTech"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000023d3fba6034
                    Extra: Last beacon: 3156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.18.1-031801-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     09DCB1F0E46935AA02BEF59
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.18.1-031801-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     7EEF5988245D414BA91F27D
depends:        cfg80211
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.18.1-031801-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3165-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     B470CC80C60FE01A481D14A
depends:        cfg80211
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/3.18.1-031801-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C8543A08D2650C7BC1B7107
depends:        
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: N
wd_disable: 1


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


iw reg set US
exit 0


##### pm-utils ##########################


[/etc/pm/config.d/blacklist] (644 root)
HOOK_BLACKLIST="wireless"


[/etc/pm/power.d/wireless] (755 root)
. "${PM_FUNCTIONS}"
which iwpriv >/dev/null 2>&1 && have_iwpriv="true"
which iwconfig >/dev/null 2>&1 && have_iwconfig="true"
get_wireless_params() {
    # $1 = interface 
    # $2 = on or off
    unset iwpriv iwconfig iwlevel
    
    # Don't do anything if we cannot find a driver for this iface.
    [ -L "/sys/class/net/$1/device/driver" ] || return 1
    # Skip if not a wireless card.
    [ -d "/sys/class/net/$1/wireless" ] || return 1
    # Also don't do anything if the device is disabled
    [ "$(cat /sys/class/net/$1/device/enabled)" = "1" ] || return 1
    driver="$(readlink "/sys/class/net/$1/device/driver")"
    driver=${driver##*/}
    case $driver in
        ipw2100) iwpriv_ac="set_power 0"
            iwpriv_batt="set_power 5"
            iwconfig_ac="power on"
            iwconfig_batt="power on";;
        ipw3945)
            iwpriv_ac="set_power 6"
            iwpriv_batt="set_power 7";;
        iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
                 iwlevel_ac=0
                 iwlevel_batt=3
              else
                 iwconfig_ac="power off"
                 iwconfig_batt="power on"
              fi;;
        *) iwconfig_ac="power off"
           iwconfig_batt="power on";;
    esac
    case $2 in
        off) [ "$iwpriv_ac" ] && iwpriv="$iwpriv_ac"
            [ "$iwconfig_ac" ] && iwconfig="$iwconfig_ac"
            [ "$iwlevel_ac" ] && iwlevel="$iwlevel_ac";;
        on) [ "$iwpriv_batt" ] && iwpriv="$iwpriv_batt"
            [ "$iwconfig_batt" ] && iwconfig="$iwconfig_batt"
            [ "$iwlevel_batt" ] && iwlevel="$iwlevel_batt";;
    esac
    return 0
}
wireless_powersave() {
    for dev in /sys/class/net/*; do
        get_wireless_params "${dev##*/}" "$1" || continue
    ret=0
    printf "Turning powersave for %s %s..." "${dev##*/}" "$1"
    if [ "$have_iwconfig" = true -a "$iwconfig" ]; then
        iwconfig "${dev##*/}" $iwconfig || ret=1
    fi
        if [ "$have_iwpriv" = true -a "$iwpriv" ]; then
        iwpriv "${dev##*/}" $iwpriv || ret=1
    fi
        if [ "$iwlevel" ]; then
        echo "$iwlevel" > "$dev/device/power_level" || ret=1
    fi
    [ "$ret" -eq 0 ] && echo Done. || echo Failed.
    done
}
case $1 in
    true) wireless_powersave off ;;
    false) wireless_powersave off ;;
    *) exit $NA ;;
esac
exit 0


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    3.435156] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.661967] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.858734] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    3.874495] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.267421] wlan0: authenticate with <MAC 'pysch42' [AC1]>
[    7.272100] wlan0: send auth to <MAC 'pysch42' [AC1]> (try 1/3)
[    7.375504] wlan0: send auth to <MAC 'pysch42' [AC1]> (try 2/3)
[    7.378146] wlan0: authenticated
[    7.378396] wlan0: associate with <MAC 'pysch42' [AC1]> (try 1/3)
[    7.382455] wlan0: RX AssocResp from <MAC 'pysch42' [AC1]> (capab=0x431 status=0 aid=3)
[    7.383369] wlan0: associated
[    7.383391] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    9.969564] wlan0: AP <MAC 'pysch42' [AC1]> changed bandwidth, new config is 2412 MHz, width 1 (2412/0 MHz)
[   10.994341] wlan0: AP <MAC 'pysch42' [AC1]> changed bandwidth, new config is 2412 MHz, width 2 (2422/0 MHz)
[   12.018963] wlan0: AP <MAC 'pysch42' [AC1]> changed bandwidth, new config is 2412 MHz, width 1 (2412/0 MHz)
[   13.043737] wlan0: AP <MAC 'pysch42' [AC1]> changed bandwidth, new config is 2412 MHz, width 2 (2422/0 MHz)
[   30.623757] wlan0: AP <MAC 'pysch42' [AC1]> changed bandwidth, new config is 2412 MHz, width 1 (2412/0 MHz)
[   33.435155] wlan0: AP <MAC 'pysch42' [AC1]> changed bandwidth, new config is 2412 MHz, width 2 (2422/0 MHz)
[   35.380694] wlan0: AP <MAC 'pysch42' [AC1]> changed bandwidth, new config is 2412 MHz, width 1 (2412/0 MHz)
[   36.420270] wlan0: AP <MAC 'pysch42' [AC1]> changed bandwidth, new config is 2412 MHz, width 2 (2422/0 MHz)


########## wireless info END ############



```[COLOR=#333333]

[/COLOR][COLOR=#333333]Thank you in advance.[/COLOR][/FONT][/SIZE]

---

### Post by praseodym on 2015-01-06
Did you try
```

sudo iwconfig wlan0 power off
```

---

### Post by evgeniy4 on 2015-06-19
I tried many solutions and problem was resolved by upgrading to 15.04 with the kernel 3.19. Wi-FI works like a charm now.

---

### Post by kelvinator on 2015-06-22
> **praseodym said:**
> Did you try
```

sudo iwconfig wlan0 power off
```

How can this be made permanent? On my laptop (Inspiron) unplugging the power disables this instruction.

---

### Post by praseodym on 2015-06-23
Open this file
```

gksudo gedit /etc/rc.local
```
and add this line before "exit 0":
```

iwconfig wlan0 power off
```
-save, close the editor and reboot.

---

