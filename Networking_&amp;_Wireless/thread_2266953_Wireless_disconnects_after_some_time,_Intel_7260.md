---
title: "Wireless disconnects after some time, Intel 7260"
date: 2015-02-26
forum: Networking &amp; Wireless
---

### Post by zak8 on 2015-02-26
I've seen a ton of threads around about problems very similar to what I'm experiencing. Usually I'm able to connect to my campus wifi, and then maybe 5-10 minutes later, sometimes longer, the connection will still be connected but internet does not work. This is usually followed by the network manager no longer listing the wireless card (driver problem?). I've tried disabling wireless-n, updating my kernel to 3.18, and using the latest intel iwlwifi driver (10 i think?). Nothing seems to be working.. any help is appreciated!

---

### Post by chili555 on 2015-02-26
Please start by giving us the result of the wireless_script described in the stickie. Thanks.

---

### Post by zak8 on 2015-02-26
```



########## wireless info START ##########


Report from: 26 Feb 2015 21:19 EST -0500


Booted last: 26 Feb 2015 21:17 EST -0500


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic


##### kernel ############################


Linux 3.18.0-031800-generic #201412071935 SMP Mon Dec 8 00:36:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4270]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 003 Device 004: ID 056a:00ec Wacom Co., Ltd 
Bus 003 Device 003: ID 0483:91d1 STMicroelectronics 
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:5720 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04f3:0254 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwlmvm                254598  0 
mac80211              697159  1 iwlmvm
iwlwifi               193813  1 iwlmvm
cfg80211              520257  3 iwlwifi,mac80211,iwlmvm
wmi                    19379  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:149.125.81.41  Bcast:149.125.83.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7937 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3373969 (3.3 MB)  TX bytes:541720 (541.7 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"busecure"  
          Mode:Managed  Frequency:5.805 GHz  Access Point: <MAC 'busecure' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=17 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:38   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         149.125.80.1    0.0.0.0         UG    0      0        0 wlan0
149.125.80.0    0.0.0.0         255.255.252.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search studentwireless.binghamton.edu


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [busecure] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    eduroam:         Infra, <MAC 'eduroam' [AC28]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 69 WPA2 Enterprise
    busecure:        Infra, <MAC 'busecure' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2 Enterprise
    busecure:        Infra, <MAC 'busecure' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2 Enterprise
    busecure:        Infra, <MAC 'busecure' [AC19]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC20]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    busecure:        Infra, <MAC 'busecure' [AC10]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC23]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC11]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise
    Connect2BU:      Infra, <MAC 'Connect2BU' [AN9]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 69
    bugaming:        Infra, <MAC 'bugaming' [AC29]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 67
    bugaming:        Infra, <MAC 'bugaming' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67
    bugaming:        Infra, <MAC 'bugaming' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    bugaming:        Infra, <MAC 'bugaming' [AC21]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 27
    Connect2BU:      Infra, <MAC 'Connect2BU' [AC18]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 25
    Connect2BU:      Infra, <MAC 'Connect2BU' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    bugaming:        Infra, <MAC 'bugaming' [AC12]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 20
    Connect2BU:      Infra, <MAC 'Connect2BU' [AC14]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 20
    bugaming:        Infra, <MAC 'bugaming' [AC24]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 19
    Connect2BU:      Infra, <MAC 'Connect2BU' [AC26]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 19
    busecure:        Infra, <MAC 'busecure' [AC22]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    bugaming:        Infra, <MAC 'bugaming' [AN22]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25
    Connect2BU:      Infra, <MAC 'Connect2BU' [AN23]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 15
    busecure:        Infra, <MAC 'busecure' [AN24]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2 Enterprise
    Connect2BU:      Infra, <MAC 'Connect2BU' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65
    *busecure:       Infra, <MAC 'busecure' [AC1]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AN27]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA2 Enterprise
    bugaming:        Infra, <MAC 'bugaming' [AC16]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 17
    eduroam:         Infra, <MAC 'eduroam' [AN29]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 14 WPA2 Enterprise
    bugaming:        Infra, <MAC 'bugaming' [AN30]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 15
    Connect2BU:      Infra, <MAC 'Connect2BU' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    Connect2BU:      Infra, <MAC 'Connect2BU' [AC15]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 19


  IPv4 Settings:
    Address:         149.125.81.41
    Prefix:          22 (255.255.252.0)
    Gateway:         149.125.80.1


    DNS:             128.226.1.11
    DNS:             128.226.20.130


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


[[/etc/NetworkManager/system-connections/bugaming]] (600 root)
[connection] id=bugaming | type=802-11-wireless
[802-11-wireless] ssid=bugaming | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Connect2BU]] (600 root)
[connection] id=Connect2BU | type=802-11-wireless | permissions=user:zak:; | autoconnect=false
[802-11-wireless] ssid=Connect2BU | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/bugaming 1]] (600 root)
[connection] id=bugaming 1 | type=802-11-wireless
[802-11-wireless] ssid=bugaming | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/busecure]] (600 root)
[connection] id=busecure | type=802-11-wireless
[802-11-wireless] ssid=busecure
[ipv4] method=auto
[ipv6] method=auto
[802-1x] ca-cert=/home/zak/.joinnow/entrust2048ca2.pem


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US: DFS-UNSET
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
          Current Frequency:5.805 GHz (Channel 161)


##### iwlist scan #######################


Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      5   APs on   Frequency:5.18 GHz (Channel 36)
      5   APs on   Frequency:5.22 GHz (Channel 44)
      2   APs on   Frequency:5.2 GHz (Channel 40)
      6   APs on   Frequency:5.765 GHz (Channel 153)
      5   APs on   Frequency:5.805 GHz (Channel 161)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'busecure' [AC1]>
                    Channel:161
                    Frequency:5.805 GHz (Channel 161)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"busecure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c6230a85
                    Extra: Last beacon: 172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 02 - Address: <MAC 'bugaming' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"bugaming"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c853aa37
                    Extra: Last beacon: 16ms ago
          Cell 03 - Address: <MAC 'bugaming' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"bugaming"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8aea025
                    Extra: Last beacon: 16ms ago
          Cell 04 - Address: <MAC 'Connect2BU' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"Connect2BU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8a80832
                    Extra: Last beacon: 4968ms ago
          Cell 05 - Address: <MAC '\00' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8539032
                    Extra: Last beacon: 4968ms ago
          Cell 06 - Address: <MAC 'Connect2BU' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"Connect2BU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8539032
                    Extra: Last beacon: 4964ms ago
          Cell 07 - Address: <MAC '\00' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8b663f6
                    Extra: Last beacon: 4652ms ago
          Cell 08 - Address: <MAC 'Connect2BU' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"Connect2BU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8b33032
                    Extra: Last beacon: 4652ms ago
          Cell 09 - Address: <MAC '' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000156c687f180
                    Extra: Last beacon: 4652ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'busecure' [AC10]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"busecure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c7d74032
                    Extra: Last beacon: 4420ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 11 - Address: <MAC 'eduroam' [AC11]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c7d74032
                    Extra: Last beacon: 4420ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 12 - Address: <MAC 'bugaming' [AC12]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"bugaming"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c7d74032
                    Extra: Last beacon: 4420ms ago
          Cell 13 - Address: <MAC '\00' [AC13]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c7d8d832
                    Extra: Last beacon: 4420ms ago
          Cell 14 - Address: <MAC 'Connect2BU' [AC14]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"Connect2BU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c7d74032
                    Extra: Last beacon: 4420ms ago
          Cell 15 - Address: <MAC 'Connect2BU' [AC15]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"Connect2BU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8585832
                    Extra: Last beacon: 4328ms ago
          Cell 16 - Address: <MAC 'bugaming' [AC16]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"bugaming"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c85d2032
                    Extra: Last beacon: 4244ms ago
          Cell 17 - Address: <MAC '\00' [AC17]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c85d2032
                    Extra: Last beacon: 4088ms ago
          Cell 18 - Address: <MAC 'Connect2BU' [AC18]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"Connect2BU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8586101
                    Extra: Last beacon: 16ms ago
          Cell 19 - Address: <MAC 'busecure' [AC19]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"busecure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c85c7aeb
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 20 - Address: <MAC 'eduroam' [AC20]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c85c1d00
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 21 - Address: <MAC 'bugaming' [AC21]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"bugaming"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c85c070a
                    Extra: Last beacon: 16ms ago
          Cell 22 - Address: <MAC 'busecure' [AC22]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"busecure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8ccb032
                    Extra: Last beacon: 1128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 23 - Address: <MAC 'eduroam' [AC23]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8ccb032
                    Extra: Last beacon: 1128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 24 - Address: <MAC 'bugaming' [AC24]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"bugaming"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8ccb032
                    Extra: Last beacon: 1128ms ago
          Cell 25 - Address: <MAC '\00' [AC25]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8ce4832
                    Extra: Last beacon: 1128ms ago
          Cell 26 - Address: <MAC 'Connect2BU' [AC26]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"Connect2BU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c8c98032
                    Extra: Last beacon: 1128ms ago
          Cell 27 - Address: <MAC '' [AC27]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:""
                    Mode:Master
                    Extra:tsf=0000003b1046a02b
                    Extra: Last beacon: 1128ms ago
          Cell 28 - Address: <MAC 'eduroam' [AC28]>
                    Channel:161
                    Frequency:5.805 GHz (Channel 161)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c83d412d
                    Extra: Last beacon: 172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 29 - Address: <MAC 'bugaming' [AC29]>
                    Channel:161
                    Frequency:5.805 GHz (Channel 161)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:"bugaming"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c83d4084
                    Extralo        Interface doesn't support scanning.


: Last beacon: 172ms ago
          Cell 30 - Address: <MAC address>
                    Channel:161
                    Frequency:5.805 GHz (Channel 161)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:"\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c83d4032
                    Extra: Last beacon: 172ms ago
          Cell 31 - Address: <MAC 'Connect2BU' [AN9]>
                    Channel:161
                    Frequency:5.805 GHz (Channel 161)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:"Connect2BU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086c83d4032
                    Extra: Last beacon: 172ms ago


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.18.0-031800-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     09DCB1F0E46935AA02BEF59
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.18.0-031800-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:96:8A:58:35:65:9D:60:E5:47:16:91:47:93:FC:20:5E:B5:9E:C0
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.18.0-031800-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     7EEF5988245D414BA91F27D
depends:        cfg80211
intree:         Y
vermagic:       3.18.0-031800-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:96:8A:58:35:65:9D:60:E5:47:16:91:47:93:FC:20:5E:B5:9E:C0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.18.0-031800-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       3.18.0-031800-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:96:8A:58:35:65:9D:60:E5:47:16:91:47:93:FC:20:5E:B5:9E:C0
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
filename:       /lib/modules/3.18.0-031800-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C8543A08D2650C7BC1B7107
depends:        
intree:         Y
vermagic:       3.18.0-031800-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:96:8A:58:35:65:9D:60:E5:47:16:91:47:93:FC:20:5E:B5:9E:C0
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
11n_disable: 1
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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1
options iwlwifi 11n_disable=0
options iwlwifi 11n_disable=1
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (755 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[    3.125573] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.845243] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    8.325974] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   18.778625] wlan0: authenticate with <MAC 'busecure' [AC1]>
[   18.781377] wlan0: send auth to <MAC 'busecure' [AC1]> (try 1/3)
[   18.782228] wlan0: authenticated
[   18.784090] wlan0: associate with <MAC 'busecure' [AC1]> (try 1/3)
[   18.787103] wlan0: RX AssocResp from <MAC 'busecure' [AC1]> (capab=0x11 status=0 aid=23)
[   18.788116] wlan0: associated
[   18.822530] wlan0: Limiting TX power to 17 dBm as advertised by <MAC 'busecure' [AC1]> (repeated 3 times)
[   19.061873] wlan0: deauthenticating from <MAC 'busecure' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   19.070641] wlan0: authenticate with <MAC 'busecure' [AC1]>
[   19.073134] wlan0: send auth to <MAC 'busecure' [AC1]> (try 1/3)
[   19.074012] wlan0: authenticated
[   19.076405] wlan0: associate with <MAC 'busecure' [AC1]> (try 1/3)
[   19.079377] wlan0: RX AssocResp from <MAC 'busecure' [AC1]> (capab=0x11 status=0 aid=23)
[   19.080245] wlan0: associated
[   19.136704] wlan0: Limiting TX power to 17 dBm as advertised by <MAC 'busecure' [AC1]>


########## wireless info END ############



```

---

### Post by chili555 on 2015-02-27
I notice that the access point you are connected to is "busecure."  There are quite a few other access points nearby with the same name, as would be expected in a Uni setting. I wonder if your wireless drops because it is attempting to roam to another access point to get a hopefully higher signal strength.

I suggest you try the process I outlined here: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by GrouchyGaijin on 2015-03-04
May I ask a related question here or should I start my own thread?

I am not trying to connect at the university, just at home, but I am having very similar problems.
In my case, the network manager says that I am connected to my router, but I cannot connect to the Internet through the WiFi or to any other devices on the WiFi network.  If I reboot the router, then it will work fine for a while before becoming unable to connect to anything again.

The name of my WiFi network is Laban.
```


########## wireless info START ##########

Report from: 04 Mar 2015 20:05 CET +0100

Booted last: 03 Mar 2015 07:37 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:10e9]
    Kernel driver in use: alx

04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Wireless-N 7260 [8086:4062]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 007: ID 5986:014c Acer, Inc 
Bus 003 Device 006: ID 8087:07dc Intel Corp. 
Bus 003 Device 005: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 003 Device 003: ID 1058:1003 Western Digital Technologies, Inc. Elements 1000 GB
Bus 003 Device 011: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 003 Device 010: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 009: ID 04a9:1904 Canon, Inc. CanoScan LiDE 100
Bus 003 Device 008: ID 04e8:3292 Samsung Electronics Co., Ltd ML-1640 Series Laser Printer
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                189813  0 
msi_wmi                13354  0 
sparse_keymap          13948  1 msi_wmi
mac80211              630669  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 msi_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:85.89.89.76  Bcast:85.89.91.255  Mask:255.255.252.0
          inet6 addr: fe80::468a:5bff:fe43:a6b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ae7b:a1ff:fee3:5e4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1716299 (1.7 MB)  TX bytes:2715004 (2.7 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Laban"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Laban' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:70   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         85.89.88.1      0.0.0.0         UG    0      0        0 eth0
85.89.88.0      0.0.0.0         255.255.252.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: wlan0  [Wi-Fi connection 1] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    dlink:           Infra, <MAC 'dlink' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    3Bredband0E26:   Infra, <MAC '3Bredband0E26' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    *Laban:          Infra, <MAC 'Laban' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    comhem51864B:    Infra, <MAC 'comhem51864B' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    ComHemE44291:    Infra, <MAC 'ComHemE44291' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2

  IPv4 Settings:
    Address:         192.168.0.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         85.89.89.76
    Prefix:          22 (255.255.252.0)
    Gateway:         85.89.88.1

    DNS:             85.89.95.254
    DNS:             85.89.68.30

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

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Laban
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/3Bredband0E26]] (600 root)
[connection] id=3Bredband0E26 | type=802-11-wireless
[802-11-wireless] ssid=3Bredband0E26 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Laben]] (600 root)
[connection] id=Laben | type=802-11-wireless
[802-11-wireless] ssid=Laben | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Laban' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Laban"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000055c691406
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'dlink' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e4d57c5a2b
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '3Bredband0E26' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"3Bredband0E26"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000502cdee5d8
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'comhem51864B' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"comhem51864B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000940e157f194
                    Extra: Last beacon: 816ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     412FF07DA992AAD938A30BE
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8DF1ECC076C2FCEAC70533
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     B81BA270CF5925E724426BD
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
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
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

coretemp

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

pcscd

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[50749.112412] wlan0: AP <MAC 'Laban' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[52245.564892] wlan0: AP <MAC 'Laban' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[53751.856056] wlan0: AP <MAC 'Laban' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[54975.032371] wlan0: authenticate with <MAC 'Laban' [AC1]>
[54975.033855] wlan0: send auth to <MAC 'Laban' [AC1]> (try 1/3)
[54975.036716] wlan0: authenticated
[54975.039955] wlan0: associate with <MAC 'Laban' [AC1]> (try 1/3)
[54975.043913] wlan0: RX AssocResp from <MAC 'Laban' [AC1]> (capab=0xc31 status=0 aid=1)
[54975.044815] wlan0: associated
[86505.007443] wlan0: AP <MAC 'Laban' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[88011.298759] wlan0: AP <MAC 'Laban' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[107223.203446] wlan0: AP <MAC 'Laban' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[108347.890227] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[108348.646231] wlan0: authenticate with <MAC 'Laban' [AC1]>
[108348.647709] wlan0: direct probe to <MAC 'Laban' [AC1]> (try 1/3)
[108348.850207] wlan0: send auth to <MAC 'Laban' [AC1]> (try 2/3)
[108348.851980] wlan0: authenticated
[108348.853428] wlan0: associate with <MAC 'Laban' [AC1]> (try 1/3)
[108348.858970] wlan0: RX AssocResp from <MAC 'Laban' [AC1]> (capab=0xc31 status=0 aid=1)
[108348.860076] wlan0: associated
[108348.860124] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[125780.716795] wlan0: deauthenticated from <MAC 'Laban' [AC1]> (Reason: 6)
[125780.732038] wlan0: authenticate with <MAC 'Laban' [AC1]>
[125780.733581] wlan0: send auth to <MAC 'Laban' [AC1]> (try 1/3)
[125780.810213] wlan0: authenticated
[125780.811493] wlan0: associate with <MAC 'Laban' [AC1]> (try 1/3)
[125780.818572] wlan0: RX AssocResp from <MAC 'Laban' [AC1]> (capab=0xc31 status=0 aid=1)
[125780.822092] wlan0: associated

########## wireless info END ############


```

---

### Post by chili555 on 2015-03-04
> wlan0: AP <MAC 'Laban' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[88011.298759] wlan0: AP <MAC 'Laban' [AC1]> changed bandwidth, new config is 2437 MHz, width 2 (2427/0 MHz)
[107223.203446] wlan0: AP <MAC 'Laban' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)Verrrry interesting!

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by GrouchyGaijin on 2015-03-04
Thank you for the reply.
Honestly, I am afraid I don't understand some of what you wrote.

I am attaching screen shots of my router configuration page.

The router make is D-Link and the model is DIR-615.
The channel is set to 6 and WPA/WPA2 is enabled. The other options are WEP and no security.
The cipher type is set to Auto (TKIP/AES)  The other options are either TKIP or AES

I ran
```
sudo iw reg get
``` in the terminal and got this:

```

country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

```

I do not know/understand what the numbers mean.  As for the country, I am in Sweden not the UK, I'm guessing when they made the router for Europe they set the UK as the default location.

---

### Post by chili555 on 2015-03-04
Try setting the CRDA to SE for Sweden.> The cipher type is set to Auto (TKIP/AES) The other options are either TKIP or AESAES only, please. I would also try Channel Width at 20 MHz only; not Auto roam all over the place so we disconnect!


[ATTACH=CONFIG]260455[/ATTACH]

And then reboot the router.

---

### Post by GrouchyGaijin on 2015-03-05
@chili555

Thank you for the help.

I followed your recommendations and set rebooted the router.
We'll see how it goes.

---

### Post by GrouchyGaijin on 2015-03-08
@chili555

Thanks again. I still had some trouble after rebooting the router (in fact I lost all wireless connectivity to the outside world), but I was able to login to the router.  So I ran their Wizard to put things back the way they were except this time I made sure that the router only used 20mhz and not 40/20mhz.  That seems to be the key, because since changing to only 20mhz I have not dropped the wireless connection once.

---

### Post by zak8 on 2015-03-09
Still haven't had any real luck. Giving it a MAC address worked short term but eventual disconnects have been inevitable. At times the wireless card does not show up under the list of pci devices, other times it does.. Recently I've been getting this system error: [https://i.imgur.com/zn1JBWx.png](https://i.imgur.com/zn1JBWx.png)

---

