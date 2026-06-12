---
title: "WiFi disconnect + won't reconnect"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by adamgallowayy on 2014-05-21
I am running Elementary OS which is based on Ubuntu 12.04 so I'm hoping you can help.

My laptop randomly disconnects from my wireless connection every so often and when I try to reconnect, it shows that it is trying to connect but then times out and asks for a password.
If I do not enter a password it retries the connection and shows another dialog box on top of the original. I have tried everything to fix this including: disabling and re-enabling my wireless adapter through a hardware switch; manually restarting network-manager through services; disabling my VPN and deleting and re-adding the network. My hardware is: HP G56 laptop and a Realtek wireless adapter. This is incredibly inconvienient as I have a lot of work to do and I am also trying to host a VNC server in order to connect remotely. It is worth noting that I use an OpenVPN VPN, run a VNC server on ports 6969 and 9696 and use custom DNS servers.

Thanks,Adam.

---

### Post by varunendra on 2014-05-22
Welcome to the forums adamgallowayy!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version), and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by adamgallowayy on 2014-05-22
Output when the internet is fine:
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

adam-HP 3.2.0-61-generic-pae i686,  elementary OS Luna, luna

CPU    : Celeron(R) Dual-Core CPU       T3500  @ 2.10GHz
Memory : 2957 MB
Uptime : 18:55:52 up 21 min,  1 user,  load average: 0.50, 0.43, 0.38


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:1467]
    Kernel driver in use: rtl8192se
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1605]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0951:1666 Kingston Technology 
Bus 002 Device 003: ID 05c8:0210 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"BTHub4-WT8N"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 BTHub4-WT8N>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:81   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface           Soft blocked  Hard blocked
0: phy0: Wireless LAN         no            no
1: hp-wifi: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
rtl8192se              94189  0 
rtlwifi                95855  1 rtl8192se
mac80211              436493  2 rtl8192se,rtlwifi
cfg80211              178877  2 rtlwifi,mac80211
wmi                    18744  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (4): ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192se     (5): debug=0 | fwlps=N | ips=Y | swenc=N | swlps=Y
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
======================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID       | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
======================o=============o===========o==============o=========o===========o==============o===========
 wlan0  [BTHub4-WT8N] | 802.11 WiFi | rtl8192se | connected    | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    BTHomeHub2-FR99: Infra, <MAC C-11 BTHomeHub2-FR99>, Freq 2442 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    SKYD6F2D:        Infra, <MAC C-12 SKYD6F2D>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    SKY11246:        Infra, <MAC C-04 SKY11246>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA
    WEAWON:          Infra, <MAC C-08 WEAWON>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    SKY4605C:        Infra, <MAC C-15 SKY4605C>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    belkin.1f2:      Infra, <MAC C-09 belkin.1f2>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    TALKTALK-7AF496: Infra, <MAC C-03 TALKTALK-7AF496>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    virginmedia7254392: Infra, <MAC C-07 virginmedia7254392>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    SKY915A4:        Infra, <MAC C-05 SKY915A4>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    BTWifi-with-FON: Infra, <MAC C-02 BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64
    BTWiFi-with-FON: Infra, <MAC C-06 BTWiFi-with-FON>, Freq 2442 MHz, Rate 54 Mb/s, Strength 60
    BTWiFi:          Infra, <MAC C-10 BTWiFi>, Freq 2442 MHz, Rate 54 Mb/s, Strength 57
    BTWiFi-with-FON: Infra, <MAC C-NA BTWiFi-with-FON 2>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    BTWiFi:          Infra, <MAC C-NA BTWiFi 2>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    *BTHub4-WT8N:    Infra, <MAC C-01 BTHub4-WT8N>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    TNCAP55BD47:     Infra, <MAC C-NA TNCAP55BD47 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    virginmedia3935756: Infra, <MAC C-NA virginmedia3935756 1>, Freq 2442 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    BTHomeHub2-NK48: Infra, <MAC C-13 BTHomeHub2-NK48>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    SKY46C0E:        Infra, <MAC C-NA SKY46C0E 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    sharon&clive network: Infra, <MAC C-NA sharon<MAC ID removed>clive network 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 14 WPA2
    Turton:          Infra, <MAC C-NA Turton 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    SKYD0DF3:        Infra, <MAC C-14 SKYD0DF3>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2

    Address:         192.168.1.65
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             213.138.101.252
    DNS:             185.19.104.45
----------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0                 | Wired       | r8169     | unavailable  | no      |           |              | <MAC eth0>
----------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 213.138.101.252
nameserver 185.19.104.45


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.12.1.213     128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
10.12.0.1       10.12.1.213     255.255.255.255 UGH   0      0        0 tun0
10.12.1.213     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
93.115.83.250   192.168.1.254   255.255.255.255 UGH   0      0        0 wlan0
128.0.0.0       10.12.1.213     128.0.0.0       UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

--- 10.12.1.213 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms


--- 213.138.101.252 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 144.518/144.824/145.130/0.306 ms

--- 185.19.104.45 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 148.118/149.177/150.237/1.127 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_GB.UTF-8")
country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 BTHub4-WT8N>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"BTHub4-WT8N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000054e1f1d214
                    Extra: Last beacon: 1028ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 BTWifi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000054e1f1d210
                    Extra: Last beacon: 1016ms ago
          Cell 03 - Address: <MAC C-03 TALKTALK-7AF496>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-7AF496"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000040a250415d
                    Extra: Last beacon: 1112ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 SKY11246>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SKY11246"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008eeda600d
                    Extra: Last beacon: 688ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 SKY915A4>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"SKY915A4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001658ff0183
                    Extra: Last beacon: 652ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 BTWiFi-with-FON>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000abcd8b798
                    Extra: Last beacon: 348ms ago
          Cell 07 - Address: <MAC C-07 virginmedia7254392>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"virginmedia7254392"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d67b8c8efd
                    Extra: Last beacon: 520ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 WEAWON>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"WEAWON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000126b217168
                    Extra: Last beacon: 396ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 belkin.1f2>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"belkin.1f2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000352ad57176
                    Extra: Last beacon: 632ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 BTWiFi>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000abcd8b185
                    Extra: Last beacon: 348ms ago
          Cell 11 - Address: <MAC C-11 BTHomeHub2-FR99>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-FR99"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000abcd8bdf4
                    Extra: Last beacon: 344ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 SKYD6F2D>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SKYD6F2D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000201c9844186
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 BTHomeHub2-NK48>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-NK48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ec407856b
                    Extra: Last beacon: 228ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 SKYD0DF3>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"SKYD0DF3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000789268183
                    Extra: Last beacon: 212ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 SKY4605C>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SKY4605C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004d4b52b183
                    Extra: Last beacon: 128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8192se]
filename:       /lib/modules/3.2.0-61-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
srcversion:     10D361B3A59BC91FDCFC605
depends:        rtlwifi,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtlwifi]
filename:       /lib/modules/3.2.0-61-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     95584F2D2B680E159E26850
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.2.0-61-generic-pae/kernel/net/mac80211/mac80211.ko
srcversion:     841C2E2496916B4F4B893C8
depends:        cfg80211
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)

[cfg80211]
filename:       /lib/modules/3.2.0-61-generic-pae/kernel/net/wireless/cfg80211.ko
srcversion:     A289A224DC04F871A44431D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Default
/etc/pm/(cnf|pw|sl) : Default


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.2.0-61-generic-pae root=UUID=cf9a66c9-4c4d-4f84-a2e3-fa4b61788d51 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.400459] audit: initializing netlink socket (disabled)
[    3.279556] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.295800] wmi: Mapper loaded
[   39.971481] rtl8192se 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   39.971492] rtl8192se 0000:02:00.0: setting latency timer to 64
[   39.983437] rtl8192se: rtl8192ce: FW Power Save off (module option)
[   40.187884] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   40.199055] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   40.199057] Loading firmware rtlwifi/rtl8192sefw.bin
[   41.397450] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   41.653861] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.654411] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.373646] wlan0: authenticate with <MAC C-01 BTHub4-WT8N> (try 1)
[   44.376232] wlan0: authenticated
[   44.376421] wlan0: associate with <MAC C-01 BTHub4-WT8N> (try 1)
[   44.379485] wlan0: RX AssocResp from <MAC C-01 BTHub4-WT8N> (capab=0x31 status=0 aid=49)
[   44.379490] wlan0: associated
[   44.400237] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.158229] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=399 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=40728 LEN=379 
[   47.175749] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=399 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=40728 LEN=379 
[   47.195997] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=399 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=40728 LEN=379 
[   55.344030] wlan0: no IPv6 routers present
[   78.496720] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=396 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=37621 LEN=376 
[   78.515725] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=396 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=37621 LEN=376 
[   78.535735] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=396 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=37621 LEN=376 
[  113.586320] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=396 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=54183 LEN=376 
[  113.603943] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=396 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=54183 LEN=376 
[  113.623892] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=396 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=54183 LEN=376 
[  123.631409] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:cc:33:bb:b7:b0:5e:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  248.503782] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:cc:33:bb:b7:b0:5e:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  268.880561] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=396 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=57122 LEN=376 
[  268.901828] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=396 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=57122 LEN=376 
[  268.918752] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.254 DST=192.168.1.65 LEN=396 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=57122 LEN=376 
[  373.762121] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:cc:33:bb:b7:b0:5e:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  498.794374] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:cc:33:bb:b7:b0:5e:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  623.514323] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:cc:33:bb:b7:b0:5e:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  748.762141] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:cc:33:bb:b7:b0:5e:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  873.601639] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:cc:33:bb:b7:b0:5e:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  998.519615] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:cc:33:bb:b7:b0:5e:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1123.521341] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:cc:33:bb:b7:b0:5e:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1248.524759] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC ID removed>:cc:33:bb:b7:b0:5e:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 

    ======== Done ========

```

I cannot replicate the bug right now...

---

### Post by varunendra on 2014-05-24
If the problem returns, the first thing to do would be to change the encryption type in the router to pure WPA2-PSK with AES (CCMP). No WPA/WPA2 mixed mode, no TKIP, which it is currently set to. Reboot the router after saving the changes.

Along with that, if required, try some driver parameters suggested in this post (replace "rtl8192**[COLOR="#FF0000"]ce[/COLOR]**" with "rtl8192**[COLOR="#0000CD"]se[/COLOR]**" in the commands) : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912)

Even if that doesn't help, you may try installing a newer driver, as mentioned here (although I can't say if it would compile successfully on your OS) : [http://ubuntuforums.org/showpost.php?p=12926946](http://ubuntuforums.org/showpost.php?p=12926946)

---

### Post by adamgallowayy on 2014-06-03
Sorry that it has taken me so long to reply. I have just got round to trying the scripts you suggested. The problem occured and I tried the first script that you posted which worked to restore my connection, however I have not tested whether the problem reoccurs, yet.

---

