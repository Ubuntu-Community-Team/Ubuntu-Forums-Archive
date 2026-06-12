---
title: "cannot connect to time warner wifi wpa2, ubuntu 14.04"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by pepeguam on 2014-09-30
I am using a lenovo thinkpad t410s with ubuntu 14.04 (realtek wlan network controller). I can connect to all secured wifi except the one which i use at home (time warner cable, ubee DDW365 Wireless modem). I can connect to it using my phones and tablets, just not with my ubuntu laptop. I have no problems connecting to other wifi (in school and using mobile tethering).

---

### Post by varunendra on 2014-10-01
Welcome to Ubuntu Forums pepeguam!

Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Run it when you are trying to connect to the home network, and it fails. You can download the script on another computer/place, then run it on the target system with "No Internet" method.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by pepeguam on 2014-10-27
```



########## wireless info START ##########


Report from: 26 Oct 2014 02:19 EDT -0400


Booted last: 26 Oct 2014 01:11 EDT -0400


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, splash, quiet


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
	Subsystem: Lenovo Device [17aa:2153]
	Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:e020]
	Kernel driver in use: rtl8192se


##### lsusb #############################


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 17ef:480d Lenovo Integrated Webcam [R5U877]
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


mxm_wmi                13021  0 
rtl8192se              63196  0 
rtl_pci                26690  1 rtl8192se
rtlwifi                63475  2 rtl_pci,rtl8192se
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  1 mxm_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2500000-f2520000 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"DDW365B7"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### nm-tool ###########################


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    DDW365B7:        Infra, <MAC 'DDW365B7' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA2
    hillsideinn:     Infra, <MAC 'hillsideinn' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    poldysnetwork:   Infra, <MAC 'poldysnetwork' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    DG860A2C82:      Infra, <MAC 'DG860A2C82' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    belkin.efe:      Infra, <MAC 'belkin.efe' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Skynet:          Infra, <MAC 'Skynet' [AC9]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WPA2
    9cd6439d91dd:    Infra, <MAC '9cd6439d91dd' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    Hillsideinn:     Infra, <MAC 'Hillsideinn' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    DIRECT-roku-433-5FF902: Infra, <MAC 'DIRECT-roku-433-5FF902' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    BigRedBadger:    Infra, <MAC 'BigRedBadger' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    HP-Print-D6-Photosmart 5520: Infra, <MAC 'HP-Print-D6-Photosmart 5520' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    hillsideinn:     Infra, <MAC 'hillsideinn' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    CSP Management - 522 Stewart: Infra, <MAC 'CSP Management - 522 Stewart' [AN13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    10 Downing Street: Infra, <MAC '10 Downing Street' [AN14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Sady's Wifi:     Infra, <MAC 'Sady's Wifi' [AN15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    'MERICA:         Infra, <MAC ''MERICA' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA
    CornellCJL104:   Infra, <MAC 'CornellCJL104' [AN17]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Jungle-guest:    Infra, <MAC 'Jungle-guest' [AN18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24
    lightlink-dryair:Infra, <MAC 'lightlink-dryair' [AN19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    Theta3:          Infra, <MAC 'Theta3' [AN20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    HP-Print-DE-ENVY 4500 series: Infra, <MAC 'HP-Print-DE-ENVY 4500 series' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    Greenacre:       Infra, <MAC 'Greenacre' [AN22]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    The Holy LAN:    Infra, <MAC 'The Holy LAN' [AN23]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    BAS_959:         Infra, <MAC 'BAS_959' [AN24]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WEP
    508Stew_floor1_1:Infra, <MAC '508Stew_floor1_1' [AN25]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless | permissions=user:pepe:;
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TVXQ]] (600 root)
[connection] id=TVXQ | type=802-11-wireless
[802-11-wireless] ssid=TVXQ | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/RedRover]] (600 root)
[connection] id=RedRover | type=802-11-wireless
[802-11-wireless] ssid=RedRover | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=ignore
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/samayhotspot]] (600 root)
[connection] id=samayhotspot | type=802-11-wireless | permissions=user:pepe:; | autoconnect=false
[802-11-wireless] ssid=samayhotspot | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore
[802-1x] ca-cert=/etc/ssl/certs/Thawte_Premium_Server_CA.pem


[[/etc/NetworkManager/system-connections/DDW365B7~]] (600 root)
[connection] id=DDW365B7 | type=802-11-wireless
[802-11-wireless] ssid=DDW365B7 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto | system-ca-certs=false


[[/etc/NetworkManager/system-connections/DDW365B7]] (600 root)
[connection] id=DDW365B7 | type=802-11-wireless
[802-11-wireless] ssid=DDW365B7 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


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


      2   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      5   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Hillsideinn' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Hillsideinn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006bc44b1d
                    Extra: Last beacon: 432ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'belkin.efe' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"belkin.efe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008326af01a
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'DDW365B7' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"DDW365B7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001afc3419e
                    Extra: Last beacon: 408ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC ''MERICA' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"'MERICA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000742b1a3e8c
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'hillsideinn' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"hillsideinn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000029daa48d1
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'DG860A2C82' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"DG860A2C82"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000077b8a80550
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '9cd6439d91dd' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"9cd6439d91dd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f89c27eba
                    Extra: Last beacon: 644ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'BigRedBadger' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"BigRedBadger"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000350268e96c1
                    Extra: Last beacon: 228ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Skynet' [AC9]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Skynet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003ed2dc0a9
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'poldysnetwork' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"poldysnetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002832a4a6f7
                    Extra: Last beacon: 180ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 11 - Address: <MAC 'DIRECT-roku-433-5FF902' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-433-5FF902"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a556f021d
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Gamehendge' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Gamehendge"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003eea27209
                    Extra: Last beacon: 184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8192se]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C53951858E34882052195CA
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_pci]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8192se]
debug: 0
fwlps: N
ips: Y
swenc: N
swlps: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1


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
blacklist acer_wmi


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
options iwlwifi 11n_disable=1


[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x10ea (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8172 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


########## wireless info END ############

```

---

### Post by pepeguam on 2015-01-05
Please any help?

---

