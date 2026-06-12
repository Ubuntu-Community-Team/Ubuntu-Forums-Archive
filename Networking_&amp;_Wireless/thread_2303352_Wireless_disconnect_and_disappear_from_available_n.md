---
title: "Wireless disconnect and disappear from available network list"
date: 2015-11-18
forum: Networking &amp; Wireless
---

### Post by Med_Amine_Jebabli on 2015-11-18
[COLOR=#111111][FONT=Ubuntu]I am running on Ubuntu 14.04 LTS.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I just installed Ubuntu and everything is fine. When I start my pc it connect to my home Wifi normally but after a random time, I am disconnected and my home wifi network disappear from the available wireless network list. When I disable/enable the netwrok I am able to reconnect again. My Laptop is Asus k555l.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is the output of lspci -knn | grep Net -A2[/FONT][/COLOR]
```
[COLOR=#111111][FONT=Consolas]03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)[/FONT][/COLOR]
Subsystem: Lite-On Communications Inc Device [11ad:0662] [COLOR=#111111][FONT=Consolas]    Kernel driver in use: ath9k[/FONT][/COLOR]
```

---

### Post by Med_Amine_Jebabli on 2015-11-19
```



########## wireless info START ##########


Report from: 19 Nov 2015 18:54 CET +0100


Booted last: 19 Nov 2015 18:46 CET +0100


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, persistent, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:0662]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
ath3k                  20480  0 
bluetooth             491520  12 bnep,ath3k,btusb,rfcomm
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  1 ath9k
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
mxm_wmi                16384  1 nouveau
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
video                  20480  3 i915,nouveau,asus_wmi


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


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3843802 (3.8 MB)  TX bytes:530925 (530.9 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"ooredooD1DBC3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'ooredooD1DBC3' [AC1]>   
          Bit Rate=58.5 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:64   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       782     1  0 18:46 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [ooredooD1DBC3] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           58 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    globalnet:       Infra, <MAC 'globalnet' [AC14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    Orange_AFFC16:   Infra, <MAC 'Orange_AFFC16' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Orange-2814:     Infra, <MAC 'Orange-2814' [AC12]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 45 WPA
    MEDIANET:        Infra, <MAC 'MEDIANET' [AC5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    IMMOBILIERE HANNIBAL: Infra, <MAC 'IMMOBILIERE HANNIBAL' [AC15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    TOPNETF1AE20EE:  Infra, <MAC 'TOPNETF1AE20EE' [AC13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA
    HEXABYTE_f7f0:   Infra, <MAC 'HEXABYTE_f7f0' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Orange-63CB:     Infra, <MAC 'Orange-63CB' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA
    ORANGE_5693:     Infra, <MAC 'ORANGE_5693' [AN9]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    TP-LINK_POCKET_3020_6A968E: Infra, <MAC 'TP-LINK_POCKET_3020_6A968E' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WEP
    HEXABYTE_b7a8:   Infra, <MAC 'HEXABYTE_b7a8' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    *ooredooD1DBC3:  Infra, <MAC 'ooredooD1DBC3' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    ORANGE_5B9A:     Infra, <MAC 'ORANGE_5B9A' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Orange-E029:     Infra, <MAC 'Orange-E029' [AN14]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    TOPNET:          Infra, <MAC 'TOPNET' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    khamassi M:      Infra, <MAC 'khamassi M' [AN16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    KHALED:          Infra, <MAC 'KHALED' [AN17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    wafa:            Infra, <MAC 'wafa' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Ooredoo-528A:    Infra, <MAC 'Ooredoo-528A' [AN19]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Skander:         Infra, <MAC 'Skander' [AN20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BnBLand:         Infra, <MAC 'BnBLand' [AC9]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Orange-4837:     Infra, <MAC 'Orange-4837' [AN22]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.1
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
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


[[/etc/NetworkManager/system-connections/ooredooD1DBC3]] (600 root)
[connection] id=ooredooD1DBC3 | type=802-11-wireless
[802-11-wireless] ssid=ooredooD1DBC3 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ORANGE_DB94]] (600 root)
[connection] id=ORANGE_DB94 | type=802-11-wireless
[802-11-wireless] ssid=ORANGE_DB94 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)


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


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ooredooD1DBC3' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"ooredooD1DBC3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007c86462341
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Orange_AFFC16' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Orange_AFFC16"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000041f1b7ec2b
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TOPNET' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"TOPNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c217be216a
                    Extra: Last beacon: 2152ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000129b41c142
                    Extra: Last beacon: 104ms ago
          Cell 05 - Address: <MAC 'MEDIANET' [AC5]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"MEDIANET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000043964184
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'HEXABYTE_b7a8' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"HEXABYTE_b7a8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000072c38da1bc
                    Extra: Last beacon: 176ms ago
          Cell 07 - Address: <MAC 'HEXABYTE_f7f0' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"HEXABYTE_f7f0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d8fb0b61bc
                    Extra: Last beacon: 172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'wafa' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"wafa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000011121cdde
                    Extra: Last beacon: 676ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'BnBLand' [AC9]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BnBLand"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f086ae155
                    Extra: Last beacon: 25612ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'TP-LINK_POCKET_3020_6A968E' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_POCKET_3020_6A968E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000198debd93d1
                    Extra: Last beacon: 40ms ago
          Cell 11 - Address: <MAC 'Orange-63CB' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Orange-63CB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001fc2a86980
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Orange-2814' [AC12]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Orange-2814"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b680da22c
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'TOPNETF1AE20EE' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"TOPNETF1AE20EE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005799c6c898
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'globalnet' [AC14]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"globalnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000516053183
                    Extra: Last beacon: 2240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'IMMOBILIERE HANNIBAL' [AC15]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"IMMOBILIERE HANNIBAL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f134638172
                    Extra: Last beacon: 2204ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'haifa' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"haifa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000521b097162
                    Extra: Last beacon: 1488ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'lassaad' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"lassaad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ae289416c
                    Extra: Last beacon: 636ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath3k]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C77B8A018F5C738ABC4CA47
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DFC03DD607884E899C8398C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0


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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[    3.506157] r8169 0000:02:00.0 eth0: link down
[    3.506202] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.521209] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.447893] wlan0: authenticate with <MAC 'ooredooD1DBC3' [AC1]>
[    4.459645] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[    4.461655] wlan0: authenticated
[    4.464569] wlan0: associate with <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[    4.468462] wlan0: RX AssocResp from <MAC 'ooredooD1DBC3' [AC1]> (capab=0x411 status=0 aid=10)
[    4.468552] wlan0: associated
[    4.468561] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  128.911999] wlan0: authenticate with <MAC 'ooredooD1DBC3' [AC1]>
[  128.928975] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[  129.059392] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 2/3)
[  129.163507] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 3/3)
[  129.267623] wlan0: authentication with <MAC 'ooredooD1DBC3' [AC1]> timed out
[  130.578312] wlan0: authenticate with <MAC 'ooredooD1DBC3' [AC1]>
[  130.594774] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[  130.658233] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 2/3)
[  130.715329] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 3/3)
[  130.772529] wlan0: authentication with <MAC 'ooredooD1DBC3' [AC1]> timed out
[  132.580322] wlan0: authenticate with <MAC 'ooredooD1DBC3' [AC1]>
[  132.596978] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[  132.676347] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 2/3)
[  132.753641] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 3/3)
[  132.816660] wlan0: authentication with <MAC 'ooredooD1DBC3' [AC1]> timed out
[  286.012117] r8169 0000:02:00.0 eth0: link down
[  286.012169] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  286.028246] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  286.870091] wlan0: authenticate with <MAC 'ooredooD1DBC3' [AC1]>
[  286.881972] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[  286.883924] wlan0: authenticated
[  286.886952] wlan0: associate with <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[  286.892178] wlan0: RX AssocResp from <MAC 'ooredooD1DBC3' [AC1]> (capab=0x411 status=0 aid=10)
[  286.892254] wlan0: associated
[  286.892263] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by Med_Amine_Jebabli on 2015-11-19
My System is updated and Here is my Wireles Info script execution

```



########## wireless info START ##########


Report from: 19 Nov 2015 18:54 CET +0100


Booted last: 19 Nov 2015 18:46 CET +0100


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, persistent, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:0662]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
ath3k                  20480  0 
bluetooth             491520  12 bnep,ath3k,btusb,rfcomm
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  1 ath9k
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
mxm_wmi                16384  1 nouveau
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
video                  20480  3 i915,nouveau,asus_wmi


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


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3843802 (3.8 MB)  TX bytes:530925 (530.9 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"ooredooD1DBC3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'ooredooD1DBC3' [AC1]>   
          Bit Rate=58.5 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:64   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       782     1  0 18:46 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [ooredooD1DBC3] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           58 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    globalnet:       Infra, <MAC 'globalnet' [AC14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    Orange_AFFC16:   Infra, <MAC 'Orange_AFFC16' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Orange-2814:     Infra, <MAC 'Orange-2814' [AC12]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 45 WPA
    MEDIANET:        Infra, <MAC 'MEDIANET' [AC5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    IMMOBILIERE HANNIBAL: Infra, <MAC 'IMMOBILIERE HANNIBAL' [AC15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    TOPNETF1AE20EE:  Infra, <MAC 'TOPNETF1AE20EE' [AC13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA
    HEXABYTE_f7f0:   Infra, <MAC 'HEXABYTE_f7f0' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Orange-63CB:     Infra, <MAC 'Orange-63CB' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA
    ORANGE_5693:     Infra, <MAC 'ORANGE_5693' [AN9]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    TP-LINK_POCKET_3020_6A968E: Infra, <MAC 'TP-LINK_POCKET_3020_6A968E' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WEP
    HEXABYTE_b7a8:   Infra, <MAC 'HEXABYTE_b7a8' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    *ooredooD1DBC3:  Infra, <MAC 'ooredooD1DBC3' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    ORANGE_5B9A:     Infra, <MAC 'ORANGE_5B9A' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Orange-E029:     Infra, <MAC 'Orange-E029' [AN14]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    TOPNET:          Infra, <MAC 'TOPNET' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    khamassi M:      Infra, <MAC 'khamassi M' [AN16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    KHALED:          Infra, <MAC 'KHALED' [AN17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    wafa:            Infra, <MAC 'wafa' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Ooredoo-528A:    Infra, <MAC 'Ooredoo-528A' [AN19]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Skander:         Infra, <MAC 'Skander' [AN20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BnBLand:         Infra, <MAC 'BnBLand' [AC9]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Orange-4837:     Infra, <MAC 'Orange-4837' [AN22]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.1
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
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


[[/etc/NetworkManager/system-connections/ooredooD1DBC3]] (600 root)
[connection] id=ooredooD1DBC3 | type=802-11-wireless
[802-11-wireless] ssid=ooredooD1DBC3 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ORANGE_DB94]] (600 root)
[connection] id=ORANGE_DB94 | type=802-11-wireless
[802-11-wireless] ssid=ORANGE_DB94 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)


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


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ooredooD1DBC3' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"ooredooD1DBC3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007c86462341
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Orange_AFFC16' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Orange_AFFC16"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000041f1b7ec2b
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TOPNET' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"TOPNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c217be216a
                    Extra: Last beacon: 2152ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000129b41c142
                    Extra: Last beacon: 104ms ago
          Cell 05 - Address: <MAC 'MEDIANET' [AC5]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"MEDIANET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000043964184
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'HEXABYTE_b7a8' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"HEXABYTE_b7a8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000072c38da1bc
                    Extra: Last beacon: 176ms ago
          Cell 07 - Address: <MAC 'HEXABYTE_f7f0' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"HEXABYTE_f7f0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d8fb0b61bc
                    Extra: Last beacon: 172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'wafa' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"wafa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000011121cdde
                    Extra: Last beacon: 676ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'BnBLand' [AC9]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BnBLand"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f086ae155
                    Extra: Last beacon: 25612ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'TP-LINK_POCKET_3020_6A968E' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_POCKET_3020_6A968E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000198debd93d1
                    Extra: Last beacon: 40ms ago
          Cell 11 - Address: <MAC 'Orange-63CB' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Orange-63CB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001fc2a86980
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Orange-2814' [AC12]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Orange-2814"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b680da22c
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'TOPNETF1AE20EE' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"TOPNETF1AE20EE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005799c6c898
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'globalnet' [AC14]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"globalnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000516053183
                    Extra: Last beacon: 2240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'IMMOBILIERE HANNIBAL' [AC15]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"IMMOBILIERE HANNIBAL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f134638172
                    Extra: Last beacon: 2204ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'haifa' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"haifa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000521b097162
                    Extra: Last beacon: 1488ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'lassaad' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"lassaad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ae289416c
                    Extra: Last beacon: 636ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath3k]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C77B8A018F5C738ABC4CA47
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DFC03DD607884E899C8398C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0


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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[    3.506157] r8169 0000:02:00.0 eth0: link down
[    3.506202] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.521209] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.447893] wlan0: authenticate with <MAC 'ooredooD1DBC3' [AC1]>
[    4.459645] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[    4.461655] wlan0: authenticated
[    4.464569] wlan0: associate with <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[    4.468462] wlan0: RX AssocResp from <MAC 'ooredooD1DBC3' [AC1]> (capab=0x411 status=0 aid=10)
[    4.468552] wlan0: associated
[    4.468561] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  128.911999] wlan0: authenticate with <MAC 'ooredooD1DBC3' [AC1]>
[  128.928975] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[  129.059392] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 2/3)
[  129.163507] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 3/3)
[  129.267623] wlan0: authentication with <MAC 'ooredooD1DBC3' [AC1]> timed out
[  130.578312] wlan0: authenticate with <MAC 'ooredooD1DBC3' [AC1]>
[  130.594774] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[  130.658233] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 2/3)
[  130.715329] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 3/3)
[  130.772529] wlan0: authentication with <MAC 'ooredooD1DBC3' [AC1]> timed out
[  132.580322] wlan0: authenticate with <MAC 'ooredooD1DBC3' [AC1]>
[  132.596978] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[  132.676347] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 2/3)
[  132.753641] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 3/3)
[  132.816660] wlan0: authentication with <MAC 'ooredooD1DBC3' [AC1]> timed out
[  286.012117] r8169 0000:02:00.0 eth0: link down
[  286.012169] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  286.028246] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  286.870091] wlan0: authenticate with <MAC 'ooredooD1DBC3' [AC1]>
[  286.881972] wlan0: send auth to <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[  286.883924] wlan0: authenticated
[  286.886952] wlan0: associate with <MAC 'ooredooD1DBC3' [AC1]> (try 1/3)
[  286.892178] wlan0: RX AssocResp from <MAC 'ooredooD1DBC3' [AC1]> (capab=0x411 status=0 aid=10)
[  286.892254] wlan0: associated
[  286.892263] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by chili555 on 2015-11-19
A number of Linux wireless drivers seem to be sensitive to the access point settings. I recommend that you check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

If these changes do not help, please try:```
sudo -i
echo "options ath9k nohwcrypt=1"  >  /etc/modprobe.d/ath9k.conf
exit
```Reboot and tell us if there is any improvement.

---

