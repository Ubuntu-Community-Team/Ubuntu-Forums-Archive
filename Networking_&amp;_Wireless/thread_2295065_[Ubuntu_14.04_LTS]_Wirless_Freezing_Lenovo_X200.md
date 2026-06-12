---
title: "[Ubuntu 14.04 LTS] Wirless Freezing Lenovo X200"
date: 2015-09-15
forum: Networking &amp; Wireless
---

### Post by woltron on 2015-09-15
Hi,

I am new in Ubuntu world (my first Linux installation). I have problems with wifi - it is completly freezing my computer for 5-10 s. At firts I thought it might be problems with RAM/Old BIOS, but I tested them and everything seems working perfectly. I found that the problem is with wifi card (everything is working just fine when I use hardware lock on wifi and use Ethernet cable to connect with internet) at the same time most problems reported with Intel Corporation PRO/Wireless 5100 AGN are about not detecting wifi or connection failures, but not with the freezing. 

I would apriciate any help, please remeber that you are talking to absolutly noob with Ubuntu/Linux and with using terminal to wii.
If you have any question or you need me to check system/logs/so on - let me know.

And yes, I am not a native speaker in English...

########## wireless info START ##########

Report from: 11 Sep 2015 14:39 CEST +0200

Booted last: 11 Sep 2015 14:30 CEST +0200

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-63-generic #103-Ubuntu SMP Fri Aug 14 21:42:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet cbontroller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Lenovo Device [17aa:20ee]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                232285  0 
mac80211              630728  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.0.0.68  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:210428962 (210.4 MB)  TX bytes:4542086 (4.5 MB)
          Interrupt:20 Memory:f2600000-f2620000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.8.27  Bcast:192.168.8.31  Mask:255.255.255.224
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14700 errors:0 dropped:1 overruns:0 frame:0
          TX packets:8213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18018793 (18.0 MB)  TX bytes:921380 (921.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Orange-640C"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Orange-640C' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.8.0     0.0.0.0         255.255.255.224 U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       969     1  0 14:30 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Orange-640C] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    COMTREND-VI-3223u-289F: Infra, <MAC 'COMTREND-VI-3223u-289F' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    MM-N:            Infra, <MAC 'MM-N' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    WEBSPACE:        Infra, <MAC 'WEBSPACE' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA
    aaaaaaaadupa:    Infra, <MAC 'aaaaaaaadupa' [AC9]>, Freq 5600 MHz, Rate 54 Mb/s, Strength 27
    NajtanszyInternet.pl_1: Infra, <MAC 'NajtanszyInternet.pl_1' [AN5]>, Freq 5320 MHz, Rate 54 Mb/s, Strength 20
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    UPC1377374:      Infra, <MAC 'UPC1377374' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    UPC0044773:      Infra, <MAC 'UPC0044773' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    UPC0048829:      Infra, <MAC 'UPC0048829' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    UPC0049069:      Infra, <MAC 'UPC0049069' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    UPC0049741:      Infra, <MAC 'UPC0049741' [AC7]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    UPC5271234:      Infra, <MAC 'UPC5271234' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    B593-4937:       Infra, <MAC 'B593-4937' [AC2]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    dlink:           Infra, <MAC 'dlink' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    MS:              Infra, <MAC 'MS' [AN18]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN20]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    UPC0041395:      Infra, <MAC 'UPC0041395' [AN21]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    BM-Employee:     Infra, <MAC 'BM-Employee' [AN22]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    *Orange-640C:    Infra, <MAC 'Orange-640C' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2

  IPv4 Settings:
    Address:         192.168.8.27
    Prefix:          27 (255.255.255.224)
    Gateway:         192.168.8.30

    DNS:             194.204.159.1
    DNS:             8.8.8.8

- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.68
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             194.204.152.34
    DNS:             194.204.159.1

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

[[/etc/NetworkManager/system-connections/Orange-640C]] (600 root)
[connection] id=Orange-640C | type=802-11-wireless
[802-11-wireless] ssid=Orange-640C | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/fasolkowe]] (600 root)
[connection] id=fasolkowe | type=802-11-wireless
[802-11-wireless] ssid=fasolkowe | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Warsaw (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)
      1   APs on   Frequency:5.6 GHz (Channel 120)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Orange-640C' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key n
                    ESSID:"Orange-640C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006d8887e9056
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'B593-4937' [AC2]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key n
                    ESSID:"B593-4937"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f949b98c91
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MM-N' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"MM-N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000047e6ce01
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'COMTREND-VI-3223u-289F' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-19 dBm  
                    Encryption key:on
                    ESSID:"COMTREND-VI-3223u-289F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b000d9938d4
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'UPC1377374' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"UPC1377374"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009a70c41ad
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'UPC Wi-Free' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009a70c4c01
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'UPC0049741' [AC7]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"UPC0049741"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001a4406195
                    Extra: Last beacon: 7396ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'UPC5271234' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption keyn
                    ESSID:"UPC5271234"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000007dee4305180
                    Extra: Last beacon: 8244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'aaaaaaaadupa' [AC9]>
                    Channel:120
                    Frequency:5.6 GHz (Channel 120)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption keyff
                    ESSID:"aaaaaaaadupa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f949ece680
                    Extra: Last beacon: 3224ms ago

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-63-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     EBFCFAE1120DBDD9F15DFA5
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-63-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:53:28:1F:E2:65:EE:3C:EA:FC:AA:3F:29:2E:21:2B:95:F0:35:9A
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-63-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8D081A0C2EE28771C5194E1
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-63-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:53:28:1F:E2:65:EE:3C:EA:FC:AA:3F:29:2E:21:2B:95:F0:35:9A
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-63-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     A45BAACCAD263355629DB7A
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-63-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:53:28:1F:E2:65:EE:3C:EA:FC:AA:3F:29:2E:21:2B:95:F0:35:9A
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
filename:       /lib/modules/3.13.0-63-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-63-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:53:28:1F:E2:65:EE:3C:EA:FC:AA:3F:29:2E:21:2B:95:F0:35:9A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
# PCI device 0x8086:0x10f5 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4237 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[  330.970663]  [<ffffffffa0535546>] iwl_dump_nic_event_log+0x346/0x370 [iwldvm]
[  330.970668]  [<ffffffffa05355b0>] iwl_nic_error+0x40/0x50 [iwldvm]
[  330.970675]  [<ffffffffa044d5b0>] iwl_trans_pcie_send_hcmd+0x5b0/0x690 [iwlwifi]
[  330.970684]  [<ffffffffa053e5a6>] iwl_dvm_send_cmd+0x46/0x110 [iwldvm]
[  330.970690]  [<ffffffffa053e811>] iwl_dvm_send_cmd_pdu+0x41/0x50 [iwldvm]
[  330.970695]  [<ffffffffa053e998>] iwlagn_txfifo_flush+0xd8/0xf0 [iwldvm]
[  330.970700]  [<ffffffffa05380d0>] iwlagn_mac_flush+0xc0/0x1b0 [iwldvm]
[  331.021461] WARNING: CPU: 0 PID: 2714 at /build/linux-hFNI9K/linux-3.13.0/drivers/net/wireless/iwlwifi/dvm/../iwl-trans.h:745 iwl_dump_nic_event_log+0x369/0x370 [iwldvm]()
[  331.021521]  [<ffffffffa0535569>] iwl_dump_nic_event_log+0x369/0x370 [iwldvm]
[  331.021526]  [<ffffffffa05355b0>] iwl_nic_error+0x40/0x50 [iwldvm]
[  331.021532]  [<ffffffffa044d5b0>] iwl_trans_pcie_send_hcmd+0x5b0/0x690 [iwlwifi]
[  331.021541]  [<ffffffffa053e5a6>] iwl_dvm_send_cmd+0x46/0x110 [iwldvm]
[  331.021547]  [<ffffffffa053e811>] iwl_dvm_send_cmd_pdu+0x41/0x50 [iwldvm]
[  331.021553]  [<ffffffffa053e998>] iwlagn_txfifo_flush+0xd8/0xf0 [iwldvm]
[  331.021557]  [<ffffffffa05380d0>] iwlagn_mac_flush+0xc0/0x1b0 [iwldvm]
[  331.021662] iwlwifi 0000:03:00.0: Log capacity -1515870811 is bogus, limit to 256 entries
[  331.021665] iwlwifi 0000:03:00.0: Log write index -1515870811 is bogus, limit to 256
[  331.021666] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[  331.072332] iwlwifi 0000:03:00.0: flush request fail
[  331.076027] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 0 [0x5a5a5a5a]
[  331.076027] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 2 [0x5a5a5a5a]
[  331.076027] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 5 [0x5a5a5a5a]
[  331.076027] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[  357.322180] iwlwifi 0000:03:00.0: Master Disable Timed Out, 100 usec
[  357.322832] iwlwifi 0000:03:00.0: Fw not loaded - dropping CMD: 1e
[  357.322836] iwlwifi 0000:03:00.0: flush request fail
[  357.328076] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  357.328521] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  357.439355] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  357.439829] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  360.637792] wlan0: authenticate with <MAC 'Orange-640C' [AC1]>
[  360.641505] wlan0: send auth to <MAC 'Orange-640C' [AC1]> (try 1/3)
[  360.644199] wlan0: authenticated
[  360.648030] wlan0: associate with <MAC 'Orange-640C' [AC1]> (try 1/3)
[  360.650738] wlan0: RX AssocResp from <MAC 'Orange-640C' [AC1]> (capab=0x411 status=0 aid=2)
[  360.652326] wlan0: associated

########## wireless info END ############

[/CODE]

---

