---
title: "Wifi connections causes laptop to freeze - ubuntu 14.04"
date: 2015-10-20
forum: Networking &amp; Wireless
---

### Post by oowej on 2015-10-20
I am experiencing some problems with wireless connections on my computer. When I connect to my schools wireless network, then the system will either freeze instantly or after a few moments, and then I need to force shutdown the computer. For whatever reason I have no problems on my home network as long as I do not disconnect from the network. no matter if I can connect to a network without the pc freezing, it will always freeze when I disconnect from it.

The wireless network adapter I have in my laptop is a Mediatek mt7630e and it would appear that the card is not supported anymore since it is not on Mediatek's site anywhere and all links to drivers from their site are dead. I managed to find drivers from other sources and have tried a couple of drivers from different sources, but that does not fix anything.

I was wondering if it was possible to solve this problem as I have read about others using Mt7630e without problems, or if I would have to get something like a USB-wifi adapter instead.

lspci:
```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Camarillo Device (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter



```here is the content of "wireless-info.txt"
```

########## wireless info START ##########

Report from: 20 Oct 2015 17:37 CEST +0200

Booted last: 20 Oct 2015 17:29 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-30-generic #34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, pci

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. Device [105b:e084]
    Kernel driver in use: mt7630e

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0489:e080 Foxconn / Hon Hai 
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
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mac80211              708608  1 mt7630e
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
cfg80211              524288  2 mac80211,mt7630e
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    20480  1 asus_wmi
video                  20480  2 i915_bpo,asus_wmi

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
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49099 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71998374 (71.9 MB)  TX bytes:2164320 (2.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"DennisWifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'DennisWifi' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-182 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:55  Invalid misc:81   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search webspeed.dk

##### network managers ##################

Installed:

    NetworkManager

Running:

root       857     1  0 17:29 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [DennisWifi] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            mt7630e
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
    altimad:         Infra, <MAC 'altimad' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    Galatasaray:     Infra, <MAC 'Galatasaray' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    TelenorD5D037:   Infra, <MAC 'TelenorD5D037' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA2
    ZyXEL2A72EA:     Infra, <MAC 'ZyXEL2A72EA' [AC7]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 68 WPA2
    TDC-AFF4:        Infra, <MAC 'TDC-AFF4' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    LasseMJ:         Infra, <MAC 'LasseMJ' [AC11]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 67 WPA2
    dx36gzu4:        Infra, <MAC 'dx36gzu4' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2
    4G Wi-Fi 3Danmark-E689: Infra, <MAC '4G Wi-Fi 3Danmark-E689' [AC4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    dnuhn7zk:        Infra, <MAC 'dnuhn7zk' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    *DennisWifi:     Infra, <MAC 'DennisWifi' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Valona17:        Infra, <MAC 'Valona17' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA2
    hboo:            Infra, <MAC 'hboo' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    Telenor30B7EB:   Infra, <MAC 'Telenor30B7EB' [AN13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2
    prtty_fly_wifi:  Infra, <MAC 'prtty_fly_wifi' [AN14]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 73 WPA2
    JN network:      Infra, <MAC 'JN network' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA2

  IPv4 Settings:
    Address:         192.168.0.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             193.162.153.164
    DNS:             194.239.134.83

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

[[/etc/NetworkManager/system-connections/DennisWifi]] (600 root)
[connection] id=DennisWifi | type=802-11-wireless
[802-11-wireless] ssid=DennisWifi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Copenhagen (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'DennisWifi' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-182 dBm  
                    Encryption key:on
                    ESSID:"DennisWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003daf928f9e
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'altimad' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:on
                    ESSID:"altimad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008d2f3987153
                    Extra: Last beacon: 192ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Galatasaray' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-182 dBm  
                    Encryption key:on
                    ESSID:"Galatasaray"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d41218580
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '4G Wi-Fi 3Danmark-E689' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=48 dBm  
                    Encryption key:on
                    ESSID:"4G Wi-Fi 3Danmark-E689"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c25539405
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'TelenorD5D037' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-190 dBm  
                    Encryption key:on
                    ESSID:"TelenorD5D037"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000090d95a87787
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'dx36gzu4' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-190 dBm  
                    Encryption key:on
                    ESSID:"dx36gzu4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ee4050118c
                    Extra: Last beacon: 1796ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'ZyXEL2A72EA' [AC7]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-191 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL2A72EA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006449e0a834
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'dnuhn7zk' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-184 dBm  
                    Encryption key:on
                    ESSID:"dnuhn7zk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005fff77299d
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'hboo' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-184 dBm  
                    Encryption key:on
                    ESSID:"hboo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000376c8815ad
                    Extra: Last beacon: 1072ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'JN network' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-184 dBm  
                    Encryption key:on
                    ESSID:"JN network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007c77c6919d
                    Extra: Last beacon: 1048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'LasseMJ' [AC11]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=70/70  Signal level=-188 dBm  
                    Encryption key:on
                    ESSID:"LasseMJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002e00fb6d11
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[mac80211]
filename:       /lib/modules/3.19.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        53:B8:7E:38:B5:24:CD:28:12:67:2F:C8:90:43:71:EA:0F:AB:DC:E5
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        53:B8:7E:38:B5:24:CD:28:12:67:2F:C8:90:43:71:EA:0F:AB:DC:E5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
apm power_off=1
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
# PCI device 0x14c3:0x7630 (mt7630e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   14.596458] <===rt2800lib_init_queues
[   14.596468] rt2800_enable_radio -7630 Dual antenna mode
[   14.610252] rt2800_init_rfcsr(): Init RF Registers MT7630
[   14.610645] rt2800_init_rfcsr: B0.R22 = 0x7c
[   14.610660] rt2800_init_rfcsr(): Init RF Registers MT7630 complete
[   14.658427] rt2800pci_toggle_irq(1):Check if PDMA is idle!
[   14.658432] rt2800pci_toggle_irq(2):Check if PDMA is idle!
[   14.670377] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.741798] wlan0: authenticate with <MAC 'DennisWifi' [AC1]>
[   15.750913] wlan0: send auth to <MAC 'DennisWifi' [AC1]> (try 1/3)
[   15.752371] wlan0: authenticated
[   15.754877] wlan0: associate with <MAC 'DennisWifi' [AC1]> (try 1/3)
[   15.758274] wlan0: RX AssocResp from <MAC 'DennisWifi' [AC1]> (capab=0x411 status=0 aid=3)
[   15.758282] ===>rt2800_sta_add:MT7630
[   15.758300] ===>rt2800_sta_add:MT7630   wcid=33
[   15.758732] ieee80211 phy0: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[   15.768985] wlan0: associated
[   15.768996] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by praseodym on 2015-10-20
Tried this one

[https://github.com/tobiasBora/MT7630E_3.16](https://github.com/tobiasBora/MT7630E_3.16)

?

---

### Post by oowej on 2015-10-21
That one does not work either. According to the "wireless-info.txt" i have kernel version 3.19 and the driver was made for 3.16. Could that maybe be the cause of the problem?

also for some reason i cannot uninstall this driver. whenever i type "make uninstall" in the terminal i get this
```
dennis@dennis-X555LAB:~/MT7630E_3.16$ make uninstall
sudo rm -rf /usr/local/MT7630E
sudo update-rc.d load_wifi.sh remove
update-rc.d: /etc/init.d/load_wifi.sh exists during rc.d purge (use -f to force)
make: *** [uninstall] Error 1


```

---

### Post by praseodym on 2015-10-21
Try reinstalling the kernel:
```

sudo apt-get install --reinstall linux-image-$(uname -r)
```

---

### Post by oowej on 2015-10-21
it cant for some reason i get the following message
```
dennis@dennis-X555LAB:~$ sudo apt-get install --reinstall linux-image$(uname -r)Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image3.19.0-30-generic
E: Couldn't find any package by regex 'linux-image3.19.0-30-generic'
```
dennis@dennis-X555LAB:~$

---

### Post by praseodym on 2015-10-21
Typo!

```
sudo apt-get install --reinstall linux-image[COLOR="#FF0000"]-[/COLOR]$(uname -r)
```

---

### Post by oowej on 2015-10-21
It reinstalled the kernel now, however the wifi still causes the laptop to freeze

---

### Post by praseodym on 2015-10-21
Please try 14.04.2 which ships kernel 3.16 from Live-CD/USB

---

### Post by oowej on 2015-10-21
just to confirm, that would be [ubuntu-14.04.2-desktop-amd64+mac.iso]("http://cdimage.ubuntu.com/releases/14.04.2/release/ubuntu-14.04.2-desktop-amd64+mac.iso") from this list right, if i have a 64 bit laptop -> [http://cdimage.ubuntu.com/releases/14.04.2/release/](http://cdimage.ubuntu.com/releases/14.04.2/release/)
?

---

### Post by praseodym on 2015-10-21
Yes

---

### Post by oowej on 2015-10-22
Hm i cant install it. my pc just boots into ubuntu instead of booting from the usb. If i set the usb as the only boot device then it just goes into the BIOS.

---

### Post by mistcloud-misty on 2015-10-27
Hello! It seems you have the exact same lspci as I do, so I'm going to assume you have a laptop similar to mine (Asus x555l?).

On that note, I was having the exact same problems as you, with a different driver installed: home wireless worked fine, with only some lag after suspend, and school network was constantly disconnecting/reconnecting and then started crashing my laptop constantly. I have managed to fix this problem, and hopefully you managed to find some way to as well while waiting for answers here. If not, I can tell you what I did to fix my problem and get my laptop working without crashes. I used a different driver which required a different kernel version so I will use the same advice here rather than guess if yours will work or not.

I followed this guide on installing the 3.13 kernel: [http://linuxg.net/how-to-install-kernel-3-13-11-7-on-ubuntu-14-04-linux-mint-17-elementary-os-0-3-pinguy-os-14-04-and-other-ubuntu-14-04-derivative-systems/](http://linuxg.net/how-to-install-kernel-3-13-11-7-on-ubuntu-14-04-linux-mint-17-elementary-os-0-3-pinguy-os-14-04-and-other-ubuntu-14-04-derivative-systems/) 

All from terminal. 

Make sure to download the driver from this page here BEFORE rebooting to log the new kernel (you will find it under more options in the ubuntu boot screen). [http://community.linuxmint.com/tutorial/view/1796](http://community.linuxmint.com/tutorial/view/1796)

Load in recovery mode first to avoid any problems with graphics drivers so you can get the wireless installed.

Open the file in file viewer and open the README file to read install instructions and info. You may have a kernel panic when the driver is installed causing a crash - I only did when installing it on 3.19 kernels, not the 3.13. Once your internet connects, you can try logging into the regular kernel or read below if you have NVIDIA graphics drivers.

This is the tricky part. 

If you have NVIDIA-346.96 drivers like I do, this kernel wreaked havoc with my system and booted into a black screen. **Only do this if you have the same driver OR if you initially boot into a black screen or cannot initialize NVIDIA in the new kernel. Replace the driver number with whichever is available for you on your proprietary drivers, and if not the same as mine, you probably won't need to remove libcuda.** I had to completely purge my nvidia drivers ```
sudo apt-get purge nvidia*
``` and reinstall the selected proprietary driver from additional drivers. I then had to purge libcuda-346 which crashes with intel on my computer (and possibly yours as well?) ```
sudo apt-get purge libcuda1-346*
``` to clear that problem. 

After that I was able to boot with some problems: glitchy login, cursor spazzing, screen floating sideways and login flashing for a few seconds until it stabilized. Far better than black screen! I still haven't fixed this but at least it boots and the wireless works.


You're almost done, at this point, if everything worked smoothly for you.

Although I was no longer crashing when using the 3.13 kernel, and the internet was 'stable' enough to stop fluttering off and on every few seconds, I would get disconnected after about 30 minutes on the campus wireless and nothing short of a reboot would get it working again. I tried to modprobe and it sent me into a kernel panic, so I would just reboot.

This problem was fortunately fixed by a very simple solution. 

Enter ```
gksudo gedit /etc/default/crda
``` into terminal to open a file. There should be a line that says REGDOMAIN= 
There is probably nothing after the =.

If you live in the US you only need to change it to REGDOMAIN=US 

If you live elsewhere, you can easily google your country's CRDA regdomain code. Save, exit. And reboot.

I haven't been disconnected or crashed since - my slow resolving DNS was fixed, and the bad internet after suspend was also fixed.

Unfortunately I can't get suspend to work when I close my laptop lid with this kernel so I have to do it manually from command line. There are still bugs to work out, but it is ultimately a lot better now. 


Hopefully this helps you or anyone else with similar problems get the wireless functioning with their computer! Good luck (:

---

