---
title: "Realtek RTL8188EE not working even after attempting forum solutions"
date: 2014-10-08
forum: Networking &amp; Wireless
---

### Post by dee8 on 2014-10-08
Hello all,

I am a complete newb to the forum and to Ubuntu 14.04 (just installed it). I just installed UBUNTU 14.04 on my Toshiba Satellite C55-A after partitioning my Win 8 hard drive. I realised that my wirless is not working; it discovers my network name, even says connected, but I get no internet. I have the Realtek RTL8188EE NIC. I logged in to this forum and attempted some potnetial solutions some of which include the following:

```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r) linux-headers-generic 

wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-

rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz 

tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz 

cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013  

make 

sudo make install 

sudo depmod -a 

sudo update-initramfs -u 

sudo cp -r firmware/* /lib/firmware


```

I also updated my Kernel to 3.16.

Neither of these solutions have worked thus far. Any help would be appreciated. Thanks and sorry for the redundancy.

---

### Post by varunendra on 2014-10-09
Welcome to the forums dee8!

Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by dee8 on 2014-10-09
Hi Varun,
Thanks for replying. Please see the output of the 'wireless-info.txt' file below.

```


########## wireless info START ##########

Report from: 09 Oct 2014 19:02 PDT -0700

Booted last: 09 Oct 2014 18:50 PDT -0700

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: alx

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0181]
    Kernel driver in use: rtl8188ee

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 10f1:1a52 Importek 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8188ee              85290  0 
rtlwifi                88787  1 rtl8188ee
mac80211              687021  2 rtlwifi,rtl8188ee
cfg80211              521225  2 mac80211,rtlwifi
wmi                    19379  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::28c:faff:fe6f:787/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5874911 (5.8 MB)  TX bytes:493982 (493.9 KB)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4ad2:24ff:fecc:e54b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:438379 (438.3 KB)  TX bytes:11956 (11.9 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"CCA46217DC82"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'CCA46217DC82' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search socal.rr.com

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [CCA46217DC82 1] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Bita:            Infra, <MAC 'Bita' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    JPgraFX Guest Network: Infra, <MAC 'JPgraFX Guest Network' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    DG1670A52:       Infra, <MAC 'DG1670A52' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    The Secret Life of JSK: Infra, <MAC 'The Secret Life of JSK' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Tim:             Infra, <MAC 'Tim' [AC20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA2
    DR.V:            Infra, <MAC 'DR.V' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA2
    ATT8w4q6Z4:      Infra, <MAC 'ATT8w4q6Z4' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    2WIRE958:        Infra, <MAC '2WIRE958' [AC17]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 60 WPA
    2WIRE129:        Infra, <MAC '2WIRE129' [AC15]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    SIMS:            Infra, <MAC 'SIMS' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    KUWAIT:          Infra, <MAC 'KUWAIT' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    Yoda's Brain:    Infra, <MAC 'Yoda's Brain' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA
    ATT233:          Infra, <MAC 'ATT233' [AC18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    KSA:             Infra, <MAC 'KSA' [AC21]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    medialink router:Infra, <MAC 'medialink router' [AC22]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    2WIRE880:        Infra, <MAC '2WIRE880' [AC2]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Guimet:          Infra, <MAC 'Guimet' [AC25]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    2WIRE280:        Infra, <MAC '2WIRE280' [AC24]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    DG1670A82:       Infra, <MAC 'DG1670A82' [AC19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    *CCA46217DC82:   Infra, <MAC 'CCA46217DC82' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 88 WPA2
    TG862G82:        Infra, <MAC 'TG862G82' [AC27]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Avila:           Infra, <MAC 'Avila' [AC23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    2WIRE450:        Infra, <MAC '2WIRE450' [AC26]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    ATT178:          Infra, <MAC 'ATT178' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    HOME_35:         Infra, <MAC 'HOME_35' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    CHANEL:          Infra, <MAC 'CHANEL' [AC16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    2WIRE250:        Infra, <MAC '2WIRE250' [AN27]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Fairytail:       Infra, <MAC 'Fairytail' [AN28]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Nekobasu:        Infra, <MAC 'Nekobasu' [AN29]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Fairytail-guest: Infra, <MAC 'Fairytail-guest' [AN30]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    2WIRE323:        Infra, <MAC '2WIRE323' [AN31]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    ATTFk4N5fi:      Infra, <MAC 'ATTFk4N5fi' [AC28]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    HP-Print-0A-Photosmart 5520: Infra, <MAC 'HP-Print-0A-Photosmart 5520' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100

  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             209.18.47.61
    DNS:             209.18.47.62

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
    Address:         192.168.0.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             209.18.47.61
    DNS:             209.18.47.62

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

[[/etc/NetworkManager/system-connections/CCA46217DC82 1]] (600 root)
[connection] id=CCA46217DC82 1 | type=802-11-wireless
[802-11-wireless] ssid=CCA46217DC82 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CCA46217DC82]] (600 root)
[connection] id=CCA46217DC82 | type=802-11-wireless
[802-11-wireless] ssid=CCA46217DC82 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.457 GHz (Channel 10)
      11   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'CCA46217DC82' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"CCA46217DC82"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000df5f6e3ff6
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '2WIRE880' [AC2]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"2WIRE880"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007e5030e542
                    Extra: Last beacon: 436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Yoda's Brain' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"Yoda's Brain"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000350105a1180
                    Extra: Last beacon: 2836ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'HOME_35' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"HOME_35"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003d1af4f918c
                    Extra: Last beacon: 2832ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'HP-Print-0A-Photosmart 5520' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-0A-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014224c0142
                    Extra: Last beacon: 3540ms ago
          Cell 06 - Address: <MAC 'ATT178' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ATT178"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000142253d64f
                    Extra: Last beacon: 3516ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'The Secret Life of JSK' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"The Secret Life of JSK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012cd5ce614e
                    Extra: Last beacon: 304ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'ATT8w4q6Z4' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"ATT8w4q6Z4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000019142c19a3
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000280b99dd610
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 10 - Address: <MAC 'JPgraFX Guest Network' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"JPgraFX Guest Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000280b99ddd93
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'DG1670A52' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"DG1670A52"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f4f8d67282
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'DR.V' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"DR.V"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003d1ad028197
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'KUWAIT' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"KUWAIT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013f0eff79f2
                    Extra: Last beacon: 168ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Bita' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Bita"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c4a550274
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC '2WIRE129' [AC15]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"2WIRE129"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000075c786b5e0
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'CHANEL' [AC16]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"CHANEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000306ecaa173
                    Extra: Last beacon: 3512ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC '2WIRE958' [AC17]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"2WIRE958"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000524b36ab98
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'ATT233' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"ATT233"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010f868c183
                    Extra: Last beacon: 1092ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'DG1670A82' [AC19]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"DG1670A82"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000009bf69146
                    Extra: Last beacon: 2140ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'Tim' [AC20]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"Tim"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000303e7a6c51
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'KSA' [AC21]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"KSA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009aad24cbc8
                    Extra: Last beacon: 1084ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'medialink router' [AC22]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"medialink router"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a3a17f0438
                    Extra: Last beacon: 5388ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'Avila' [AC23]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Avila"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012a9b110191
                    Extra: Last beacon: 864ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC '2WIRE280' [AC24]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"2WIRE280"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000020f0788181
                    Extra: Last beacon: 2288ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'Guimet' [AC25]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Guimet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003d3b5609183
                    Extra: Last beacon: 2844ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC '2WIRE450' [AC26]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"2WIRE450"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e685eda181
                    Extra: Last beacon: 2808ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC 'TG862G82' [AC27]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"TG862G82"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003d1aca4cf67
                    Extra: Last beacon: 2428ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'ATTFk4N5fi' [AC28]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"ATTFk4N5fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026b73e6b183
                    Extra: Last beacon: 1816ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8188ee]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     F236B2D61DC22E55AE16BE1
depends:        rtlwifi,mac80211
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtlwifi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
author:         Benjamin Porter    <BenjaminPorter86@gmail.com>
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     60362F48D23628B07F1F32E
depends:        mac80211,cfg80211
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D86AFD97E7F71C59777C05F
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8188ee]
debug: 0
fwlps: N
ips: N
msi: N
swenc: N
swlps: N

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

[/etc/modprobe.d/modprobe.conf]
options rtl8192ce ips=1
options rtl8192ce fwlps=0
options rtl8192ce swenc=1

[/etc/modprobe.d/rtl8188ee.conf]
options rtl8188ee ips=0 fwlps=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   15.004782] rtl8188ee: rtl8188ee: Power Save off (module option)
[   15.004786] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   15.004793] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   15.336818] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.337023] rtlwifi: wireless switch is on
[   21.820065] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.661416] wlan0: authenticate with <MAC 'CCA46217DC82' [AC1]>
[   23.671691] wlan0: direct probe to <MAC 'CCA46217DC82' [AC1]> (try 1/3)
[   23.875673] wlan0: send auth to <MAC 'CCA46217DC82' [AC1]> (try 2/3)
[   23.877427] wlan0: authenticated
[   23.879657] wlan0: associate with <MAC 'CCA46217DC82' [AC1]> (try 1/3)
[   23.895538] wlan0: RX AssocResp from <MAC 'CCA46217DC82' [AC1]> (capab=0xc11 status=0 aid=3)
[   23.895648] wlan0: associated
[   23.895685] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by varunendra on 2014-10-10
Everything looks fine as per the report. If you unplug the Ethernet cable, wait for a minute, then try to ping your router or an internet address, don't you get a reply?

For example, try this in a terminal after disconnecting the Ethernet cable -
```
ping -c4 192.168.0.1
ping -c4 8.8.8.8
```
Do both of these succeed to get replies?

---

### Post by dee8 on 2014-10-10
Varun,

Here is what I get:

```

dur@dur-Satellite-C55-A:~$ ping -c4 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3022ms

dur@dur-Satellite-C55-A:~$ ping -c4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms


```

---

### Post by dee8 on 2014-10-19
I'm not sure if any of the posted solutions solved the problem, but when I restarted my system today, wi-fi started to work. Thanks for all your help.

---

