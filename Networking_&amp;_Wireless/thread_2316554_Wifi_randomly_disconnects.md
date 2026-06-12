---
title: "Wifi randomly disconnects"
date: 2016-03-09
forum: Networking &amp; Wireless
---

### Post by chris-fp-jakins on 2016-03-09
This has been happening since I installed Ubuntu. My computer will still show that it is connected, but my internet will stop working and say it's not connected. It doesn't reconnect automatically and requires me to disconnect and reconnect manually.

Any idea what I should do here? Thanks in advance..

---

### Post by howefield on 2016-03-09
Thread moved to the "*Networking & Wireless*" forum.

Read this [sticky]("http://ubuntuforums.org/showthread.php?t=370108") for starters.

---

### Post by chris-fp-jakins on 2016-03-09
Ok I tried that

Here is the output of the wireless script:

[ATTACH]267723[/ATTACH]

```


########## wireless info START ##########


Report from: 09 Mar 2016 13:59 CST -0600


Booted last: 09 Mar 2016 13:58 CST -0600


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device [1043:859f]
	Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: AzureWave Device [1a3b:2161]
	Kernel driver in use: rtl8821ae


##### lsusb #############################


Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 001 Device 002: ID 0461:4e26 Primax Electronics, Ltd 
Bus 001 Device 004: ID 13d3:3414 IMC Networks 
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


eeepc_wmi              16384  0 
asus_wmi               24576  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
rtl8821ae             229376  0 
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                73728  2 rtl_pci,rtl8821ae
mac80211              712704  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              524288  2 mac80211,rtlwifi
video                  20480  1 asus_wmi
wmi                    20480  1 asus_wmi


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
          Interrupt:20 Memory:f7200000-f7220000 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15714944 (15.7 MB)  TX bytes:834452 (834.4 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"TreeTopIsLove"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'TreeTopIsLove' [AC8]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:70   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       900     1  0 13:58 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [TreeTopIsLove] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8821ae
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Duval_Villas_Pool: Infra, <MAC 'Duval_Villas_Pool' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    Roman Empire:    Infra, <MAC 'Roman Empire' [AC13]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 97 WPA2
    AJJ Pad:         Infra, <MAC 'AJJ Pad' [AC4]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 94 WPA2
    NETGEAR05:       Infra, <MAC 'NETGEAR05' [AC14]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 80 WPA2
    Mongolian Empire:Infra, <MAC 'Mongolian Empire' [AC20]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 70 WPA2
    NETGEAR21-5G:    Infra, <MAC 'NETGEAR21-5G' [AC21]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 70 WPA2
    ANYTHING:        Infra, <MAC 'ANYTHING' [AC5]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    Duval_Villas_Pool: Infra, <MAC 'Duval_Villas_Pool' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA
    NETGEAR69:       Infra, <MAC 'NETGEAR69' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA2
    318 Wireless:    Infra, <MAC '318 Wireless' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
    TP-LINK_2.4GHz_08E3F1: Infra, <MAC 'TP-LINK_2.4GHz_08E3F1' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    NETGEAR05-5G:    Infra, <MAC 'NETGEAR05-5G' [AC49]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 64 WPA2
    NETGEAR31:       Infra, <MAC 'NETGEAR31' [AC43]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA2
    ROOM 235:        Infra, <MAC 'ROOM 235' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2
    wasabii:         Infra, <MAC 'wasabii' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA2
    BecauseFi:       Infra, <MAC 'BecauseFi' [AN16]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    NETGEAR17:       Infra, <MAC 'NETGEAR17' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2
    belkin.132.5GHz: Infra, <MAC 'belkin.132.5GHz' [AC18]>, Freq 5260 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    NETGEAR61-5G:    Infra, <MAC 'NETGEAR61-5G' [AC22]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 59 WPA2
    TheChamber:      Infra, <MAC 'TheChamber' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA
    chen's palace:   Infra, <MAC 'chen's palace' [AN21]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    Mail Order Wifi: Infra, <MAC 'Mail Order Wifi' [AC19]>, Freq 5300 MHz, Rate 54 Mb/s, Strength 50 WPA2
    NETGEAR66-arlo_246996: Infra, <MAC 'NETGEAR66-arlo_246996' [AN23]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 57 WPA2
    NETGEAR87:       Infra, <MAC 'NETGEAR87' [AN24]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 45 WPA2
    NETGEAR05-5G:    Infra, <MAC 'NETGEAR05-5G' [AC48]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Texas:           Infra, <MAC 'Texas' [AN26]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    NETGEAR13:       Infra, <MAC 'NETGEAR13' [AN27]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 40 WPA2
    NETGEAR61:       Infra, <MAC 'NETGEAR61' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    12345671:        Infra, <MAC '12345671' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WEP
    Bulya:           Infra, <MAC 'Bulya' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WEP
    318.guests:      Infra, <MAC '318.guests' [AC45]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74
    Two Broke Bros-guest: Infra, <MAC 'Two Broke Bros-guest' [AN32]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 67
    AnAlarmingNumberOfBees-guest: Infra, <MAC 'AnAlarmingNumberOfBees-guest' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    *TreeTopIsLove:  Infra, <MAC 'TreeTopIsLove' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 88 WPA2
    Mail Order Wifi: Infra, <MAC 'Mail Order Wifi' [AC30]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA2
    NETGEAR05:       Infra, <MAC 'NETGEAR05' [AC31]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 70 WPA2
    Al Roker Guest:  Infra, <MAC 'Al Roker Guest' [AC24]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA2
    ugly:            Infra, <MAC 'ugly' [AC26]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    DG1670A92:       Infra, <MAC 'DG1670A92' [AC32]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    Al Roker:        Infra, <MAC 'Al Roker' [AC28]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2
    Casa de Lil:     Infra, <MAC 'Casa de Lil' [AC29]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA2
    BachelorPad:     Infra, <MAC 'BachelorPad' [AC33]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 60 WPA2
    the cloud mountain: Infra, <MAC 'the cloud mountain' [AC34]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 57 WPA2
    318 Wireless.media: Infra, <MAC '318 Wireless.media' [AC38]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Pottery Barn Teens: Infra, <MAC 'Pottery Barn Teens' [AN45]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    wasabiii:        Infra, <MAC 'wasabiii' [AC40]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Have you seen my bear Tibbers?: Infra, <MAC 'Have you seen my bear Tibbers?' [AC25]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    ENTernet:        Infra, <MAC 'ENTernet' [AC35]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2
    Casa de Lil:     Infra, <MAC 'Casa de Lil' [AC39]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 42 WPA2
    AnAlarmingNumberOfBees: Infra, <MAC 'AnAlarmingNumberOfBees' [AC23]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Robo:            Infra, <MAC 'Robo' [AN51]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA2
    NETGEAR87:       Infra, <MAC 'NETGEAR87' [AC27]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 44 WPA2
    JandT:           Infra, <MAC 'JandT' [AC36]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    MMwireless:      Infra, <MAC 'MMwireless' [AC42]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Pottery Barn Teens-guest: Infra, <MAC 'Pottery Barn Teens-guest' [AN55]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    belkin.528.guests: Infra, <MAC 'belkin.528.guests' [AN56]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 50


  IPv4 Settings:
    Address:         192.168.1.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


[[/etc/NetworkManager/system-connections/TreeTopIsLove]] (600 root)
[connection] id=TreeTopIsLove | type=802-11-wireless
[802-11-wireless] ssid=TreeTopIsLove | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Al Roker]] (600 root)
[connection] id=Al Roker | type=802-11-wireless
[802-11-wireless] ssid=Al Roker | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     24 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      9   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      14   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      5   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      2   APs on   Frequency:5.22 GHz (Channel 44)
      1   APs on   Frequency:5.26 GHz (Channel 52)
      1   APs on   Frequency:5.2 GHz (Channel 40)
      1   APs on   Frequency:5.3 GHz (Channel 60)
      5   APs on   Frequency:5.765 GHz (Channel 153)
      1   APs on   Frequency:5.785 GHz (Channel 157)


wlan0     Scan completed :
          Cell 01 - Address: <MAC '318 Wireless' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"318 Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a57529863
                    Extra: Last beacon: 24908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '12345671' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"12345671"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002f160014b
                    Extra: Last beacon: 68ms ago
          Cell 03 - Address: <MAC 'ROOM 235' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"ROOM 235"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003982a36ff
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'AJJ Pad' [AC4]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"AJJ Pad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000723e37cf3
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'ANYTHING' [AC5]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"ANYTHING"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002f90b6743
                    Extra: Last beacon: 1588ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'TheChamber' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"TheChamber"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c20f07fdf2
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Duval_Villas_Pool' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Duval_Villas_Pool"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a59ec3e26
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'TreeTopIsLove' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"TreeTopIsLove"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c24d2b9e36
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'AnAlarmingNumberOfBees-guest' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"AnAlarmingNumberOfBees-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c2112d591f
                    Extra: Last beacon: 2484ms ago
          Cell 10 - Address: <MAC 'Bulya' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Bulya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c21365d2c5
                    Extra: Last beacon: 68ms ago
          Cell 11 - Address: <MAC 'Duval_Villas_Pool' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"Duval_Villas_Pool"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c211bdb4ca
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'wasabii' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"wasabii"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000024f2dd5ed
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Roman Empire' [AC13]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Roman Empire"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ed0726270
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'NETGEAR05' [AC14]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR05"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002eb361136
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'NETGEAR61' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR61"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000055228a10b
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'NETGEAR69' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR69"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c212d48db2
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'NETGEAR17' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR17"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a55131180
                    Extra: Last beacon: 29436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'belkin.132.5GHz' [AC18]>
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"belkin.132.5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007d9bc303a
                    Extra: Last beacon: 2928ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'Mail Order Wifi' [AC19]>
                    Channel:60
                    Frequency:5.3 GHz (Channel 60)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Mail Order Wifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a56fdb03b
                    Extra: Last beacon: 2152ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'Mongolian Empire' [AC20]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Mongolian Empire"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ed0c195fb
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'NETGEAR21-5G' [AC21]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR21-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000722be6443
                    Extra: Last beacon: 1120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'NETGEAR61-5G' [AC22]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR61-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000054f2e065d
                    Extra: Last beacon: 25940ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'AnAlarmingNumberOfBees' [AC23]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"AnAlarmingNumberOfBees"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c211400763
                    Extra: Last beacon: 1260ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC 'Al Roker Guest' [AC24]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Al Roker Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000034c876dc27
                    Extra: Last beacon: 224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'Have you seen my bear Tibbers?' [AC25]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Have you seen my bear Tibbers?"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c22d97e92d
                    Extra: Last beacon: 296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC 'ugly' [AC26]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ugly"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001f914199
                    Extra: Last beacon: 260ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC 'NETGEAR87' [AC27]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR87"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001f0efa713
                    Extra: Last beacon: 7624ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'Al Roker' [AC28]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Al Roker"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000034c876e9e4
                    Extra: Last beacon: 220ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 29 - Address: <MAC 'Casa de Lil' [AC29]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Casa de Lil"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000033637afbd
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 30 - Address: <MAC 'Mail Order Wifi' [AC30]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Mail Order Wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a58e4c4d2
                    Extra: Last beacon: 7900ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 31 - Address: <MAC 'NETGEAR05' [AC31]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR05"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002327b508f
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 32 - Address: <MAC 'DG1670A92' [AC32]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"DG1670A92"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004e07d7a143
                    Extra: Last beacon: 264ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 33 - Address: <MAC 'BachelorPad' [AC33]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"BachelorPad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c212f71153
                    Extra: Last beacon: 244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 34 - Address: <MAC 'the cloud mountain' [AC34]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"the cloud mountain"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ed6a8e01
                    Extra: Last beacon: 24908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 35 - Address: <MAC 'ENTernet' [AC35]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"ENTernet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c2123d7472
                    Extra: Last beacon: 24908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 36 - Address: <MAC 'JandT' [AC36]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"JandT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c211a0e188
                    Extra: Last beacon: 1708ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 37 - Address: <MAC '' [AC37]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Mode:Master
                    Extra:tsf=00000012fb08802b
                    Extra: Last beacon: 29088ms ago
          Cell 38 - Address: <MAC '318 Wireless.media' [AC38]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"318 Wireless.media"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ce6d0e01b
                    Extra: Last beacon: 28772ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 39 - Address: <MAC 'Casa de Lil' [AC39]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Casa de Lil"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003347bfa96
                    Extra: Last beacon: 24908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 40 - Address: <MAC 'wasabiii' [AC40]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"wasabiii"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000024e00a054
                    Extra: Last beacon: 25940ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 41 - Address: <MAC '' [AC41]>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Mode:Master
                    Extra:tsf=000000096bc6102b
                    Extra: Last beacon: 25612ms ago
          Cell 42 - Address: <MAC 'MMwireless' [AC42]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"MMwireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000024b816f
                    Extra: Last beacon: 1376ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 43 - Address: <MAC 'NETGEAR31' [AC43]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR31"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000013956743d
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 44 - Address: <MAC 'Yonce89-2.4G' [AC44]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Yonce89-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000522576ba6
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 45 - Address: <MAC '318.guests' [AC45]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"318.guests"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a58c78173
                    Extra: Last beacon: 7572ms ago
          Cell 46 - Address: <MAC 'PlayFi2Device00B2B3' [AC46]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"PlayFi2Device00B2B3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c213310128
                    Extra: Last beacon: 6800ms ago
          Cell 47 - Address: <MAC 'belkin.132' [AC47]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"belkin.132"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007d9b5ccf7
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 48 - Address: <MAC 'NETGEAR05-5G' [AC48]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR05-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004e4a12144
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 49 - Address: <MAC 'NETGEAR05-5G' [AC49]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR05-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002eb77903a
                    Extra: Last beacon: 1088ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     5FCDD84BF572D3F1AFBE47E
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)


[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     A25DC6D8C53D55DA133BC49
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: Y
swenc: N
swlps: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


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


[/etc/modprobe.d/iwlwidi.conf]
options iwlwifi 11n_disable=1


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x153b (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    8.537901] rtl8821ae 0000:03:00.0: enabling device (0000 -> 0003)
[    8.550993] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[    8.555468] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.555615] rtlwifi: rtlwifi: wireless switch is on
[   12.860401] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.111674] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.717277] wlan0: authenticate with <MAC 'TreeTopIsLove' [AC8]>
[   14.717607] wlan0: send auth to <MAC 'TreeTopIsLove' [AC8]> (try 1/3)
[   14.722988] wlan0: authenticated
[   14.725818] wlan0: associate with <MAC 'TreeTopIsLove' [AC8]> (try 1/3)
[   14.731406] wlan0: RX AssocResp from <MAC 'TreeTopIsLove' [AC8]> (capab=0x431 status=0 aid=2)
[   14.731588] wlan0: associated
[   14.731603] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############
```

Maybe that's better

---

### Post by chris-fp-jakins on 2016-03-24
Bump. Would really appreciate help here, if anyone can find the time!

---

