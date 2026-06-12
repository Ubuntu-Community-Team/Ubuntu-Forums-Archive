---
title: "Intel PRO/Wireless 4965 AG/AGN: WiFi keeps disconnecting 14.04"
date: 2014-11-26
forum: Networking &amp; Wireless
---

### Post by rothbow on 2014-11-26
Hi all...
I recently installed 14.04 coming from 13.04...now I can't get the WiFi to stay connected, had no problems with raring, but now it connects for a few minutes then drops out to 0mbps or disconnects altogether.
I've tried all the possible cures that I could understand, (pretty new at the terminal) but nothing has worked so far, so I'm hoping someone can point me in the right direction.
I am running a wep connection, but it's shared and I'm not able to change it until the person upstream gets onboard... I've also tried to isolate my connection from other sources in the neighborhood, but that didn't help either. I get a good strong signal at first, then nothing...

```



    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

fu 3.13.0-40-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
Memory : 1974 MB
Uptime : 21:47:42 up 42 min,  2 users,  load average: 0.51, 0.16, 0.13


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
    Subsystem: Lenovo ThinkPad T61/R61 [17aa:20b9]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4230] (rev 61)
    Subsystem: Intel Corporation Lenovo ThinkPad T51 [8086:1110]
    Kernel driver in use: iwl4965


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 17ef:1004 Lenovo Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. BCM2045B (BDC-2) [Bluetooth Controller]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"11FX09120830"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 11FX09120830>   
          Bit Rate=36 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:91   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: hci0: Bluetooth                     no            no
1: tpacpi_bluetooth_sw: Bluetooth      no            no
2: phy0: Wireless LAN                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwl4965               106859  0 
iwlegacy               88016  1 iwl4965
mac80211              546051  2 iwl4965,iwlegacy
cfg80211              409394  3 iwl4965,iwlegacy,mac80211
wmi                    18673  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): 
iwl4965       (5): 
iwlegacy      (2): 
mac80211      (5): 
wmi           (2): 


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=======================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID        | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=======================o=============o=========o==============o=========o===========o==============o===========
 <BT Device>           | Bluetooth   | bluez   | disconnected | no      |           |              |           
-----------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0  [11FX09120830] | 802.11 WiFi | iwl4965 | connected    | yes     | 11 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    SC:              Infra, <MAC C-02 SC>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2
    Waldoheadstart:  Infra, <MAC C-06 Waldoheadstart>, Freq 2447 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Whats my SSID again?: Infra, <MAC C-12 Whats my SSID again?>, Freq 2452 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    VAP-Corporate:   Infra, <MAC C-09 VAP-Corporate>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA
    CDS MIDCOAST:    Infra, <MAC C-03 CDS MIDCOAST>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    VAP-Guest:       Infra, <MAC C-08 VAP-Guest>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA
    DDW36119C:       Infra, <MAC C-NA DDW36119C 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Waldoheadstart:  Infra, <MAC C-05 Waldoheadstart>, Freq 2427 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    HELL:            Infra, <MAC C-04 HELL>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Comtrend238D:    Infra, <MAC C-NA Comtrend238D 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Hawking_300N_Extender: Infra, <MAC C-NA Hawking_300N_Extender 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    Living Room Chromecast: Infra, <MAC C-10 Living Room Chromecast>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    *11FX09120830:   Infra, <MAC C-01 11FX09120830>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WEP
    FSS:             Infra, <MAC C-07 FSS>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2

    Address:         192.168.1.37
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-----------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                  | Wired       | e1000e  | unavailable  | no      |           |              | <MAC eth0>
-----------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

07B408772799         : ssid=07B408772799 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
11FX09120830         : ssid=11FX09120830 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 
3tides-guest         : ssid=3tides-guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
anghill              : ssid=anghill | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
ArchangelWIFI        : ssid=ArchangelWIFI | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
attwifi              : ssid=attwifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Belfast Free Library : ssid=Belfast Free Library | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
BluestreakWIFI       : ssid=BluestreakWIFI | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Clover               : ssid=Clover | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
DemoWiFi             : ssid=DemoWiFi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Front Street Shipyard Guest : ssid=Front Street Shipyard Guest | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
linksys              : ssid=linksys | bssid=<MAC ID removed> | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Miramar              : ssid=Miramar | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Miramar 1            : ssid=Miramar | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MW-guest             : ssid=MW-guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
OFFICE               : ssid=OFFICE | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Scallions            : ssid=Scallions | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Scallions-guest      : ssid=Scallions-guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
stpeter              : ssid=stpeter | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Verizon XT1080 1248  : ssid=Verizon XT1080 1248 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search westell.com


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 1.088/1.307/1.527/0.222 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.053/0.054/0.056/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     24 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)

          Current Frequency=2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 11FX09120830>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"11FX09120830"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000067e4bfc8ea
                    Extra: Last beacon: 40ms ago
          Cell 02 - Address: <MAC C-02 SC>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e410dd3b8
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 CDS MIDCOAST>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"CDS MIDCOAST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000443777478b
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 HELL>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HELL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ef58ad4ee
                    Extra: Last beacon: 17656ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Waldoheadstart>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Waldoheadstart"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009498578390
                    Extra: Last beacon: 17656ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 Waldoheadstart>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Waldoheadstart"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007216cfec64
                    Extra: Last beacon: 1984ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 FSS>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"FSS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000d33b180
                    Extra: Last beacon: 19824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 VAP-Guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"VAP-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000b5824a
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 VAP-Corporate>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"VAP-Corporate"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000b5c906
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 Living Room Chromecast>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"Living Room Chromecast"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002feecd142
                    Extra: Last beacon: 2048ms ago
          Cell 11 - Address: <MAC C-11 Front Street Shipyard Guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Front Street Shipyard Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000e439180
                    Extra: Last beacon: 2032ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 Whats my SSID again?>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Whats my SSID again?"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b15bb72b5
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 Belfast Yoga>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Belfast Yoga"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000093f869f19c
                    Extra: Last beacon: 1920ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwl4965]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware:       iwlwifi-4965-2.ucode
version:        in-tree:
srcversion:     52A3B1E68D22B0078326AC5
depends:        iwlegacy,cfg80211,mac80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
version:        in-tree:
srcversion:     400F302BE5C25B3C98A6CE8
depends:        mac80211,cfg80211
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/mac80211/mac80211.ko
srcversion:     123C230E7AC85A31E4CA28B
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=8
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-40-generic root=UUID=f8269f59-1bdd-4969-8463-7b50ebe8694b ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.381529] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.382349] audit: initializing netlink socket (disabled)
[    7.519515] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.343597] wmi: Mapper loaded
[   20.625850] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   20.625854] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   20.625897] iwl4965 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   20.625986] iwl4965 0000:03:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   20.662073] iwl4965 0000:03:00.0: device EEPROM VER=0x36, CALIB=0x5
[   20.701991] iwl4965 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   20.702040] iwl4965 0000:03:00.0: irq 49 for MSI/MSI-X
[   20.780140] thinkpad_acpi: http://ibm-acpi.sf.net/
[   21.076298] iwl4965 0000:03:00.0: loaded firmware version 228.61.2.24
[   21.087642] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   23.037132] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.522363] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.522711] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.324684] wlan0: authenticate with <MAC C-01 11FX09120830>
[   28.333402] wlan0: direct probe to <MAC C-01 11FX09120830> (try 1/3)
[   28.536126] wlan0: send auth to <MAC C-01 11FX09120830> (try 2/3)
[   28.538915] wlan0: authenticated
[   28.539179] iwl4965 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   28.539184] iwl4965 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   28.539187] iwl4965 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   28.540054] wlan0: associate with <MAC C-01 11FX09120830> (try 1/3)
[   28.542466] wlan0: RX AssocResp from <MAC C-01 11FX09120830> (capab=0x411 status=0 aid=2)
[   28.567524] wlan0: associated
[   28.567561] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  285.848314] iwl4965 0000:03:00.0: Error sending C_REM_STA: time out after 500ms.
[  285.848330] iwl4965 0000:03:00.0: Error removing station <MAC C-01 11FX09120830>
[  286.348287] iwl4965 0000:03:00.0: Error sending C_RXON: time out after 500ms.
[  286.348302] iwl4965 0000:03:00.0: Error setting new RXON (-110)
[  286.972315] iwl4965 0000:03:00.0: Error sending C_SCAN: time out after 500ms.
[  286.988270] iwl4965 0000:03:00.0: Queue 4 stuck for 2500 ms.
[  286.988295] iwl4965 0000:03:00.0: On demand firmware reload
[  287.472263] iwl4965 0000:03:00.0: Error sending C_WEPKEY: time out after 500ms.
[  287.472288] wlan0: failed to remove key (0, <MAC ID removed>) from hardware (-110)
[  287.473668] iwl4965 0000:03:00.0: Timeout stopping DMA channel 1 [0xa5a5a5a0]
[  287.474993] iwl4965 0000:03:00.0: Timeout stopping DMA channel 3 [0xa5a5a5a0]
[  287.476308] iwl4965 0000:03:00.0: Timeout stopping DMA channel 4 [0xa5a5a5a0]
[  287.476308] iwl4965 0000:03:00.0: Timeout stopping DMA channel 6 [0xa5a5a5a0]
[  302.347003] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  355.348380] WARNING: CPU: 0 PID: 770 at /build/buildd/linux-3.13.0/net/mac80211/key.c:605 ieee80211_free_keys+0x150/0x160 [mac80211]()
[  355.348387] Modules linked in: cuse rfcomm bnep binfmt_misc snd_hda_codec_analog arc4 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev coretemp kvm_intel kvm pcmcia thinkpad_acpi nvram snd_seq_midi snd_seq_midi_event snd_rawmidi joydev serio_raw r852 sm_common nand iwl4965 yenta_socket nand_ecc r592 iwlegacy snd_hda_intel nand_bch pcmcia_rsrc lpc_ich snd_hda_codec mac80211 bch nand_ids snd_hwdep mtd memstick pcmcia_core snd_pcm cfg80211 snd_seq snd_page_alloc snd_seq_device i915 btusb bluetooth drm_kms_helper drm snd_timer mei_me mei i2c_algo_bit snd wmi soundcore video mac_hid parport_pc ppdev lp parport psmouse ahci libahci sdhci_pci firewire_ohci sdhci firewire_core e1000e crc_itu_t ptp pps_core
[  355.349027]  [<c1599932>] ? __netlink_ns_capable+0x32/0x40
[  355.349036]  [<c15839f4>] rtnetlink_rcv_msg+0x84/0x1f0
[  355.349055]  [<c1583970>] ? rtnetlink_rcv+0x30/0x30
[  355.349064]  [<c159d736>] netlink_rcv_skb+0x86/0xa0
[  355.349072]  [<c1583961>] rtnetlink_rcv+0x21/0x30
[  355.349080]  [<c159cdeb>] netlink_unicast+0xbb/0x170
[  355.349089]  [<c159d107>] netlink_sendmsg+0x267/0x700
[  355.349098]  [<c159a59b>] ? netlink_rcv_wake+0x3b/0x50
[  403.254380] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  405.032302] wlan0: authenticate with <MAC C-01 11FX09120830>
[  405.032419] wlan0: send auth to <MAC C-01 11FX09120830> (try 1/3)
[  405.034310] wlan0: authenticated
[  405.034449] iwl4965 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  405.034453] iwl4965 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  405.034456] iwl4965 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  405.040077] wlan0: associate with <MAC C-01 11FX09120830> (try 1/3)
[  405.042444] wlan0: RX AssocResp from <MAC C-01 11FX09120830> (capab=0x411 status=0 aid=2)
[  405.069124] wlan0: associated
[  405.069158] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  590.724234] iwl4965 0000:03:00.0: Queue 2 stuck for 2500 ms.
[  590.724260] iwl4965 0000:03:00.0: On demand firmware reload
[  591.032294] iwl4965 0000:03:00.0: Error sending C_REM_STA: time out after 500ms.
[  591.032310] iwl4965 0000:03:00.0: Error removing station <MAC C-01 11FX09120830>
[  591.033698] iwl4965 0000:03:00.0: Timeout stopping DMA channel 1 [0xa5a5a5a0]
[  591.035022] iwl4965 0000:03:00.0: Timeout stopping DMA channel 3 [0xa5a5a5a0]
[  591.036341] iwl4965 0000:03:00.0: Timeout stopping DMA channel 4 [0xa5a5a5a0]
[  591.036347] iwl4965 0000:03:00.0: Timeout stopping DMA channel 6 [0xa5a5a5a0]
[  591.536302] iwl4965 0000:03:00.0: Error sending C_WEPKEY: time out after 500ms.
[  591.536319] wlan0: failed to remove key (0, <MAC ID removed>) from hardware (-110)
[  591.537046] iwl4965 0000:03:00.0: Request scan called when driver not ready.
[  789.888833] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  791.985906] wlan0: authenticate with <MAC C-01 11FX09120830>
[  791.986109] wlan0: send auth to <MAC C-01 11FX09120830> (try 1/3)
[  791.988625] wlan0: authenticated
[  791.988902] iwl4965 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  791.988912] iwl4965 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  791.988919] iwl4965 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  791.992122] wlan0: associate with <MAC C-01 11FX09120830> (try 1/3)
[  791.994426] wlan0: RX AssocResp from <MAC C-01 11FX09120830> (capab=0x411 status=0 aid=2)
[  792.019642] wlan0: associated
[  792.019686] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  853.116707] wlan0: deauthenticating from <MAC C-01 11FX09120830> by local choice (reason=3)
[ 2529.062241] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2530.890912] wlan0: authenticate with <MAC C-01 11FX09120830>
[ 2530.891009] wlan0: send auth to <MAC C-01 11FX09120830> (try 1/3)
[ 2530.892950] wlan0: authenticated
[ 2530.893103] iwl4965 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2530.893108] iwl4965 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2530.893111] iwl4965 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2530.896149] wlan0: associate with <MAC C-01 11FX09120830> (try 1/3)
[ 2530.898626] wlan0: RX AssocResp from <MAC C-01 11FX09120830> (capab=0x411 status=0 aid=2)
[ 2530.924455] wlan0: associated
[ 2530.924500] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========

```

Thanks...

---

### Post by jeremy31 on 2014-11-28
Can you change the router security from WEP to WPA2-AES, Linux doesn't like WEP or TKIP for a lot of wifi cards

---

### Post by rothbow on 2014-11-28
> **jeremy31 said:**
> Can you change the router security from WEP to WPA2-AES, Linux doesn't like WEP or TKIP for a lot of wifi cards

Thank you for the reply.... No I can't change, it's shared and I need to get the primary to change. It did work fine with raring....wish I could just change back.

---

### Post by jeremy31 on 2014-11-28
> **rothbow said:**
> Thank you for the reply.... No I can't change, it's shared and I need to get the primary to change. It did work fine with raring....wish I could just change back.

Well the argument for WPA2-AES is that the security is much better than WEP and I think it supports faster transfers.  If nothing else find a Netgear WN1000RP or similar, it is a network extender that you can connect to a WEP router and you can connect to it using WPA2-AES.  I use my WN1000RP to extend the range on my cellular wifi hotspot in the house

---

### Post by rothbow on 2014-11-28
> **jeremy31 said:**
> Well the argument for WPA2-AES is that the security is much better than WEP and I think it supports faster transfers.  If nothing else find a Netgear WN1000RP or similar, it is a network extender that you can connect to a WEP router and you can connect to it using WPA2-AES.  I use my WN1000RP to extend the range on my cellular wifi hotspot in the house

Looks cool...and not too much $....thanks

---

