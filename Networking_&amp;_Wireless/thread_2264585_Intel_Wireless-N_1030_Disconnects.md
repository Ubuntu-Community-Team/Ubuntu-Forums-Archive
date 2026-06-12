---
title: "Intel Wireless-N 1030 Disconnects"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by EzerchE on 2015-02-08
Hello i have installed Ubuntu 14.04 on my HP DV6 6020st everything works great except Wifi, it sometimes disconnects while i am using my computer. I upgraded to 14.10 but nothing changed.

Here is my wireless-info.txt report i have generated.

```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


ezerche-HP-Pavilion-dv6-Notebook-PC 3.16.0-30-generic x86_64,  Ubuntu 14.10, utopic


CPU    : Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
Memory : 7931 MB
Uptime : 20:10:05 up 32 min,  2 users,  load average: 0,53, 0,47, 0,58




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1657]
	Kernel driver in use: r8169
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008b] (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5315]
	Kernel driver in use: iwlwifi




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 006: ID 8086:0189 Intel Corp. 
Bus 002 Device 004: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:e258 Suyin Corp. HP TrueVision HD Integrated Webcam
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"Ez-NET"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC C-01 Ez-NET>   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface             Soft blocked  Hard blocked
1: hp-wifi: Wireless LAN        no            no
2: hp-bluetooth: Bluetooth      no            no
3: phy0: Wireless LAN           no            no
4: hci0: Bluetooth              no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwldvm                236430  0 
mac80211              660592  1 iwldvm
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
iwlwifi               183038  1 iwldvm
cfg80211              510218  3 iwlwifi,mac80211,iwldvm
wmi                    19193  1 hp_wmi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (13): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_monitor=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | uapsd_disable=N | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID  | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
=================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [Ez-NET] | 802.11 WiFi | iwlwifi | connected   | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>


    TTNET_ZyXEL:     Infra, <MAC C-06 TTNET_ZyXEL>, Freq 2422 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    chidogo:         Infra, <MAC C-21 chidogo>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    TTNET_AirTies_Air5650_6436: Infra, <MAC C-07 TTNET_AirTies_Air5650_6436>, Freq 2427 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    Tilgin-uUYTkQQphb4d: Infra, <MAC C-03 Tilgin-uUYTkQQphb4d>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    ZyXEL11:         Infra, <MAC C-11 ZyXEL11>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA
    TURKTEKS:        Infra, <MAC C-10 TURKTEKS>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    SEC_LinkShare_21102f: Infra, <MAC C-02 SEC_LinkShare_21102f>, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2
    TTNET_AirTies_Air5650_746R: Infra, <MAC C-NA TTNET_AirTies_Air5650_746R 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    SEF:             Infra, <MAC C-15 SEF>, Freq 2447 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    AIRTIES_RT-205:  Infra, <MAC C-NA AIRTIES_RT-205 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA
    arslan:          Infra, <MAC C-09 arslan>, Freq 2432 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    SUPERONLINE_WiFi_2067: Infra, <MAC C-13 SUPERONLINE_WiFi_2067>, Freq 2442 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Sun123:          Infra, <MAC C-05 Sun123>, Freq 2422 MHz, Rate 54 Mb/s, Strength 47 WPA
    Tilgin-DkADrSSxP64F: Infra, <MAC C-04 Tilgin-DkADrSSxP64F>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA
    ZyXEL:           Infra, <MAC C-22 ZyXEL>, Freq 2472 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Tilgin-6tPpc4bRbuyZ: Infra, <MAC C-NA Tilgin-6tPpc4bRbuyZ 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    chidogo-guest:   Infra, <MAC C-20 chidogo-guest>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    HP-Print-E8-Officejet Pro 8610: Infra, <MAC C-23 HP-Print-E8-Officejet Pro 8610>, Freq 2472 MHz, Rate 54 Mb/s, Strength 37
    *Ez-NET:         Infra, <MAC C-01 Ez-NET>, Freq 2417 MHz, Rate 54 Mb/s, Strength 73 WPA WPA2
    NE:              Infra, <MAC C-NA NE 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    DIRECT-6mPhilips TV: Infra, <MAC C-19 DIRECT-6mPhilips TV>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2
    TTNET_AirTies_Air5650_F767: Infra, <MAC C-08 TTNET_AirTies_Air5650_F767>, Freq 2427 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Yusuf:           Infra, <MAC C-NA Yusuf 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Tirtil96:        Infra, <MAC C-NA Tirtil96 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    DAMLA:           Infra, <MAC C-NA DAMLA 1>, Freq 2472 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    SUPERONLINE_Wi-Fi_1661: Infra, <MAC C-NA SUPERONLINE_Wi-Fi_1661 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    EV-AGI:          Infra, <MAC C-NA EV-AGI 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    NilornWorldWide: Infra, <MAC C-NA NilornWorldWide 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    CLK:             Infra, <MAC C-14 CLK>, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    SUPERONLINE_WiFi_2401: Infra, <MAC C-17 SUPERONLINE_WiFi_2401>, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Tilgin-yhPKcPZqSSzY: Infra, <MAC C-18 Tilgin-yhPKcPZqSSzY>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA
    GARDENYA-SATIS:  Infra, <MAC C-16 GARDENYA-SATIS>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA2
    TTNET_ZTE_5926:  Infra, <MAC C-NA TTNET_ZTE_5926 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2


    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4
-----------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0            | Wired       | r8169   | unavailable | no      |           |              | <MAC eth0>
-----------------+-------------+---------+-------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


Ez-NET               : ssid=Ez-NET | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SEC_LinkShare_21102f : ssid=SEC_LinkShare_21102f | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 3.466/6.952/10.439/3.487 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.045/0.051/0.058/0.009 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : tr_TR.UTF-8)
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), NO-IR
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
	(5170 - 5250 @ 40), (3, 20), NO-IR
	(5735 - 5835 @ 40), (3, 20), NO-IR




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.417 GHz (Channel 2)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Ez-NET>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Ez-NET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000707aba3f
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 SEC_LinkShare_21102f>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"SEC_LinkShare_21102f"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000175342a4b
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Tilgin-uUYTkQQphb4d>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-uUYTkQQphb4d"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000020d82bd6e
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Tilgin-DkADrSSxP64F>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-DkADrSSxP64F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007cb314e66
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Sun123>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Sun123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000883673bc9
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 TTNET_ZyXEL>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"TTNET_ZyXEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007030ec630
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 TTNET_AirTies_Air5650_6436>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"TTNET_AirTies_Air5650_6436"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000088343dc35
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 TTNET_AirTies_Air5650_F767>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"TTNET_AirTies_Air5650_F767"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000088346f128
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 arslan>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"arslan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000162e621b0
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 TURKTEKS>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"TURKTEKS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001952eca6215
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 ZyXEL11>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL11"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008838551c0
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 Tilgin-dZUhDbZ4665S>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-dZUhDbZ4665S"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000881802a34
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 SUPERONLINE_WiFi_2067>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"SUPERONLINE_WiFi_2067"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008840daf69
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 CLK>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"CLK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008830fd989
                    Extra: Last beacon: 736ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 SEF>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"SEF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000088418b139
                    Extra: Last beacon: 720ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 GARDENYA-SATIS>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"GARDENYA-SATIS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008818404d7
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC C-17 SUPERONLINE_WiFi_2401>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"SUPERONLINE_WiFi_2401"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000731fe169
                    Extra: Last beacon: 704ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC C-18 Tilgin-yhPKcPZqSSzY>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-yhPKcPZqSSzY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000010ff2958
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC C-19 DIRECT-6mPhilips TV>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-6mPhilips TV"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000071a5817e1
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC C-20 chidogo-guest>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"chidogo-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000883349834
                    Extra: Last beacon: 144ms ago
          Cell 21 - Address: <MAC C-21 chidogo>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"chidogo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000883349f50
                    Extra: Last beacon: 140ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC C-22 ZyXEL>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004328c6176
                    Extra: Last beacon: 104ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC C-23 HP-Print-E8-Officejet Pro 8610>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-E8-Officejet Pro 8610"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000088338df34
                    Extra: Last beacon: 68ms ago
          Cell 24 - Address: <MAC C-24 Tilgin-bDt6TYXC8HT4>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-bDt6TYXC8HT4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000088495b173
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[iwldvm]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     092C5F7885F1C7B9B99605B
depends:        iwlwifi,mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D421794D4F30DF3A540FD24
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[hp_wmi]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     2BEC5DCE5B3A6695D374C6A
depends:        wmi,sparse-keymap


[iwlwifi]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
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
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     D335B9FC08B25C4ADA0BD33
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/wireless/cfg80211.ko
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x008b (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modprobe.d]
iwlmvm.conf       : options iwlmvm power_scheme=1
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


[/etc/pm/power.d/wireless]




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/vmlinuz-3.16.0-30-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.029183] Initializing cgroup subsys net_cls
[    0.029193] Initializing cgroup subsys net_prio
[    0.757626] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.758104] audit: initializing netlink subsys (disabled)
[    0.879733] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.860614] wmi: Mapper loaded
[   12.406089] iwlwifi 0000:0d:00.0: can't disable ASPM; OS doesn't have ASPM control
[   12.406212] iwlwifi 0000:0d:00.0: irq 54 for MSI/MSI-X
[   13.064882] iwlwifi 0000:0d:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   14.042904] iwlwifi 0000:0d:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   14.042907] iwlwifi 0000:0d:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   14.042909] iwlwifi 0000:0d:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   14.042911] iwlwifi 0000:0d:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   14.043004] iwlwifi 0000:0d:00.0: L1 Enabled - LTR Disabled
[   14.208633] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   24.631225] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.289882] iwlwifi 0000:0d:00.0: L1 Enabled - LTR Disabled
[   28.296707] iwlwifi 0000:0d:00.0: Radio type=0x2-0x2-0x1
[   28.364886] iwlwifi 0000:0d:00.0: L1 Enabled - LTR Disabled
[   28.371729] iwlwifi 0000:0d:00.0: Radio type=0x2-0x2-0x1
[   28.442560] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.133196] wlan0: authenticate with <MAC C-01 Ez-NET>
[   30.146356] wlan0: send auth to <MAC C-01 Ez-NET> (try 1/3)
[   30.148262] wlan0: authenticated
[   30.151587] wlan0: associate with <MAC C-01 Ez-NET> (try 1/3)
[   30.155340] wlan0: RX AssocResp from <MAC C-01 Ez-NET> (capab=0x431 status=0 aid=1)
[   30.162148] wlan0: associated
[   30.162172] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.368022] wlan0: deauthenticating from <MAC C-01 Ez-NET> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   30.384812] wlan0: authenticate with <MAC C-01 Ez-NET>
[   30.396717] wlan0: send auth to <MAC C-01 Ez-NET> (try 1/3)
[   30.398931] wlan0: authenticated
[   30.399514] wlan0: associate with <MAC C-01 Ez-NET> (try 1/3)
[   30.403213] wlan0: RX AssocResp from <MAC C-01 Ez-NET> (capab=0x431 status=0 aid=1)
[   30.406263] wlan0: associated
[   78.580780] wlan0: authenticate with <MAC C-01 Ez-NET>
[   78.591595] wlan0: send auth to <MAC C-01 Ez-NET> (try 1/3)
[   78.593559] wlan0: authenticated
[   78.596183] wlan0: associate with <MAC C-01 Ez-NET> (try 1/3)
[   78.599918] wlan0: RX AssocResp from <MAC C-01 Ez-NET> (capab=0x431 status=0 aid=1)
[   78.607523] wlan0: associated
[  242.003803] WARNING: CPU: 0 PID: 78 at /build/buildd/linux-3.16.0/net/wireless/reg.c:1806 reg_process_hint+0x2d1/0x460 [cfg80211]()
[  242.003807] Modules linked in: nls_iso8859_1 ctr ccm bnep rfcomm uvcvideo videobuf2_vmalloc videobuf2_memops hid_logitech_dj arc4 videobuf2_core iwldvm v4l2_common usbhid videodev media uas mac80211 usb_storage hid hp_wmi intel_rapl sparse_keymap snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp radeon iwlwifi snd_hda_intel rtsx_pci_ms btusb i915 coretemp memstick snd_hda_controller bluetooth snd_hda_codec kvm snd_hwdep 6lowpan_iphc cfg80211 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul snd_rawmidi ttm ghash_clmulni_intel snd_seq drm_kms_helper drm snd_seq_device snd_timer i2c_algo_bit aesni_intel snd soundcore aes_x86_64 lrw gf128mul shpchp glue_helper lpc_ich mei_me video ablk_helper mei joydev cryptd hp_accel serio_raw lis3lv02d
[  242.003910]  input_polldev mac_hid wmi parport_pc ppdev lp parport rtsx_pci_sdmmc psmouse ahci libahci r8169 rtsx_pci mii
[  818.258386] wlan0: deauthenticated from <MAC C-01 Ez-NET> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[  818.328718] wlan0: authenticate with <MAC C-01 Ez-NET>
[  818.341010] wlan0: send auth to <MAC C-01 Ez-NET> (try 1/3)
[  818.444651] wlan0: send auth to <MAC C-01 Ez-NET> (try 2/3)
[  818.446546] wlan0: authenticated
[  818.448683] wlan0: associate with <MAC C-01 Ez-NET> (try 1/3)
[  818.454351] wlan0: RX AssocResp from <MAC C-01 Ez-NET> (capab=0x431 status=0 aid=1)
[  818.461198] wlan0: associated
[ 1384.981889] wlan0: deauthenticated from <MAC C-01 Ez-NET> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[ 1423.354779] iwlwifi 0000:0d:00.0: RF_KILL bit toggled to disable radio.
[ 1423.355022] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[ 1423.355059] iwlwifi 0000:0d:00.0: Not sending command - RF KILL
[ 1424.364835] iwlwifi 0000:0d:00.0: RF_KILL bit toggled to enable radio.
[ 1424.584528] iwlwifi 0000:0d:00.0: L1 Enabled - LTR Disabled
[ 1424.591428] iwlwifi 0000:0d:00.0: Radio type=0x2-0x2-0x1
[ 1424.674207] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1425.370615] wlan0: authenticate with <MAC C-01 Ez-NET>
[ 1425.381697] wlan0: send auth to <MAC C-01 Ez-NET> (try 1/3)
[ 1425.383583] wlan0: authenticated
[ 1425.391399] wlan0: associate with <MAC C-01 Ez-NET> (try 1/3)
[ 1425.395286] wlan0: RX AssocResp from <MAC C-01 Ez-NET> (capab=0x431 status=0 aid=1)
[ 1425.401473] wlan0: associated
[ 1425.401501] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1895.062408] wlan0: deauthenticated from <MAC C-01 Ez-NET> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[ 1895.133875] wlan0: authenticate with <MAC C-01 Ez-NET>
[ 1895.147272] wlan0: send auth to <MAC C-01 Ez-NET> (try 1/3)
[ 1895.149469] wlan0: authenticated
[ 1895.153664] wlan0: associate with <MAC C-01 Ez-NET> (try 1/3)
[ 1895.160041] wlan0: RX AssocResp from <MAC C-01 Ez-NET> (capab=0x431 status=0 aid=1)
[ 1895.165075] wlan0: associated
[ 1928.563366] WARNING: CPU: 0 PID: 78 at /build/buildd/linux-3.16.0/net/wireless/reg.c:1806 reg_process_hint+0x2d1/0x460 [cfg80211]()
[ 1928.563371] Modules linked in: nls_iso8859_1 ctr ccm bnep rfcomm uvcvideo videobuf2_vmalloc videobuf2_memops hid_logitech_dj arc4 videobuf2_core iwldvm v4l2_common usbhid videodev media uas mac80211 usb_storage hid hp_wmi intel_rapl sparse_keymap snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_codec_generic x86_pkg_temp_thermal intel_powerclamp radeon iwlwifi snd_hda_intel rtsx_pci_ms btusb i915 coretemp memstick snd_hda_controller bluetooth snd_hda_codec kvm snd_hwdep 6lowpan_iphc cfg80211 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul snd_rawmidi ttm ghash_clmulni_intel snd_seq drm_kms_helper drm snd_seq_device snd_timer i2c_algo_bit aesni_intel snd soundcore aes_x86_64 lrw gf128mul shpchp glue_helper lpc_ich mei_me video ablk_helper mei joydev cryptd hp_accel serio_raw lis3lv02d
[ 1928.563475]  input_polldev mac_hid wmi parport_pc ppdev lp parport rtsx_pci_sdmmc psmouse ahci libahci r8169 rtsx_pci mii


	======== Done ========
```

---

### Post by EzerchE on 2015-02-09
I have resolved the problem by this way;

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

[COLOR=#333333][FONT=UbuntuRegular]Change wireless settings to match the screenshots;[/FONT][/COLOR]

[IMG]http://i.stack.imgur.com/hqxoKm.png[/IMG][IMG]http://i.stack.imgur.com/iEqNkm.png[/IMG]

[COLOR=#333333][FONT=UbuntuRegular]modify this file: sudo /etc/modprobe.d/iwlwifi.conf change[/FONT][/COLOR]

options iwlwifi 11n_disable=1
[COLOR=#333333][FONT=UbuntuRegular]To:[/FONT][/COLOR]
options iwlwifi 11n_disable=1 iwlwifi bt_coex_active=0

reboot
[http://askubuntu.com/questions/363126/slow-wifi-after-with-centrino-wireless-n-1030-rainbow-peak](http://askubuntu.com/questions/363126/slow-wifi-after-with-centrino-wireless-n-1030-rainbow-peak)

---

### Post by jeremy31 on 2015-02-09
If you want or need more speed from wifi, you might want to try 11n_disable=8

---

### Post by Hadaka on 2015-02-09
Great job !!

Please mark your thread SOLVED so the searchers can find it
thanks.

---

### Post by EzerchE on 2015-02-10
> **jeremy31 said:**
> If you want or need more speed from wifi, you might want to try 11n_disable=8

I tried 11n_disable=0 and speed increased well, whats different between 0 and 8 ?

---

### Post by jeremy31 on 2015-02-10
> **EzerchE said:**
> I tried 11n_disable=0 and speed increased well, whats different between 0 and 8 ?

11n_disable=8 enables agg tx which usually helps with intel wifi cards when they are using 11n but 0 doesn't
somewhere between the release of Ubuntu 12.04 and 14.04 a change was made that drastically reduced the speed on some intel cards when 11n_disable=8 is not used
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630)

---

### Post by EzerchE on 2015-02-10
Thanks! My internet speed 10mbit more increased!

---

