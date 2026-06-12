---
title: "Lenovo Ubuntu wifi broken"
date: 2016-04-01
forum: Networking &amp; Wireless
---

### Post by apollon2 on 2016-04-01
I have a Lenovo B50-30, I installed ubuntu, I had wifi when installing, but after that whenever I try to connect it says connecting but never connects, I 've tried almost everything nothing works.
Here is the wireless info
please help

```
########## wireless info START ##########


Report from: 02 Apr 2016 00:45 EEST +0300


Booted last: 01 Apr 2016 22:38 EEST +0300


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380c]
    Kernel driver in use: r8169


04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be


##### lsusb #############################


Bus 003 Device 002: ID 8087:07e6 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:579c Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 008: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath9k_htc              77824  0 
ath9k_common           36864  1 ath9k_htc
ath9k_hw              466944  2 ath9k_common,ath9k_htc
ath                    32768  3 ath9k_common,ath9k_htc,ath9k_hw
rtl8723be              90112  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              729088  4 rtl_pci,rtlwifi,ath9k_htc,rtl8723be
cfg80211              540672  5 ath,ath9k_common,mac80211,rtlwifi,ath9k_htc
snd_soc_rt5640        114688  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               102400  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_pcm_dmaengine,snd_hda_core


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116610 errors:0 dropped:47 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:232434794 (232.4 MB)  TX bytes:9971004 (9.9 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1982580 (1.9 MB)  TX bytes:356480 (356.4 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search lan


##### network managers ##################


Installed:


    NetworkManager


Running:


root       789     1  0 Apr01 ?        00:00:15 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Soultana:        Infra, <MAC 'Soultana' [AC2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 54 WPA
    ChristosPanagiota: Infra, <MAC 'ChristosPanagiota' [AC5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 37 WPA2
    OTE990A29:       Infra, <MAC 'OTE990A29' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    OTE WiFi Fon:    Infra, <MAC 'OTE WiFi Fon' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44
    Natasa:          Infra, <MAC 'Natasa' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA
    desp123:         Infra, <MAC 'desp123' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    home2:           Infra, <MAC 'home2' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    Forthnet-1575C:  Infra, <MAC 'Forthnet-1575C' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    SEC_LinkShare_da3094: Infra, <MAC 'SEC_LinkShare_da3094' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.70
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


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


[[/etc/NetworkManager/system-connections/home2]] (600 root)
[connection] id=home2 | type=802-11-wireless
[802-11-wireless] ssid=home2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Forthnet-1575C]] (600 root)
[connection] id=Forthnet-1575C | type=802-11-wireless
[802-11-wireless] ssid=Forthnet-1575C | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Athens (based on set time zone)


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


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'home2' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"home2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ca3fed34c
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Soultana' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Soultana"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000040cd905e20
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Forthnet-1575C' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Forthnet-1575C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001964433e1
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Natasa' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Natasa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000058a6594425
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'ChristosPanagiota' [AC5]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"ChristosPanagiota"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000181fe3c0bbf
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'SEC_LinkShare_da3094' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SEC_LinkShare_da3094"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000296963f7f
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'OTE990A29' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"OTE990A29"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000044ebd662ed
                    Extra: Last beacon: 4964ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'OTE WiFi Fon' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"OTE WiFi Fon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000044ebd6717c
                    Extra: Last beacon: 4964ms ago


##### module infos ######################


[ath9k_htc]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     81DFB3391B095616853B954
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           blink:Enable LED blink on activity (int)


[ath9k_common]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     619327754B562F78060585E
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F987BF2735D3EF13C4E4E3D
depends:        ath
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512


[rtl8723be]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     F4844EEE911CB18A8B2934B
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512
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
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)


[rtl8723_common]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A888EFDC516033207A503FA
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     F4CACC5FCAEBE7C22930A24
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     FBF6EA073A00B4F3836226E
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k_htc]
blink: 1
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0


[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
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
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[ 4945.269499] r8169 0000:03:00.0 eth0: link down
[ 4946.892335] r8169 0000:03:00.0 eth0: link up
[ 4947.729228] r8169 0000:03:00.0 eth0: link down
[ 4949.362623] r8169 0000:03:00.0 eth0: link up
[ 4950.210022] r8169 0000:03:00.0 eth0: link down
[ 4951.833164] r8169 0000:03:00.0 eth0: link up
[ 4952.680272] r8169 0000:03:00.0 eth0: link down (repeated 2 times)
[ 4964.363621] r8169 0000:03:00.0 eth0: link up
[ 5143.253844] wlan0: authenticate with <MAC 'home2' [AC1]>
[ 5143.275604] wlan0: send auth to <MAC 'home2' [AC1]> (try 1/3)
[ 5143.280015] wlan0: authenticated
[ 5143.280817] wlan0: associate with <MAC 'home2' [AC1]> (try 1/3)
[ 5143.288662] wlan0: RX AssocResp from <MAC 'home2' [AC1]> (capab=0x411 status=0 aid=4)
[ 5143.289275] wlan0: associated
[ 5188.854133] wlan0: deauthenticating from <MAC 'home2' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 6337.728413] r8169 0000:03:00.0 eth0: link down
[ 6347.616951] wlan0: authenticate with <MAC 'home2' [AC1]>
[ 6347.638232] wlan0: send auth to <MAC 'home2' [AC1]> (try 1/3)
[ 6347.641665] wlan0: authenticated
[ 6347.644459] wlan0: associate with <MAC 'home2' [AC1]> (try 1/3)
[ 6347.650764] wlan0: RX AssocResp from <MAC 'home2' [AC1]> (capab=0x411 status=0 aid=4)
[ 6347.651340] wlan0: associated
[ 6389.820800] r8169 0000:03:00.0 eth0: link down
[ 6391.444072] r8169 0000:03:00.0 eth0: link up
[ 6392.822919] wlan0: deauthenticating from <MAC 'home2' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 7422.185159] wlan0: authenticate with <MAC 'home2' [AC1]>
[ 7422.207204] wlan0: send auth to <MAC 'home2' [AC1]> (try 1/3)
[ 7422.210266] wlan0: authenticated
[ 7422.212293] wlan0: associate with <MAC 'home2' [AC1]> (try 1/3)
[ 7422.217751] wlan0: RX AssocResp from <MAC 'home2' [AC1]> (capab=0x411 status=0 aid=4)
[ 7422.218340] wlan0: associated
[ 7467.661878] wlan0: deauthenticating from <MAC 'home2' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 7545.193530] r8169 0000:03:00.0 eth0: link down
[ 7559.287958] wlan0: authenticate with <MAC 'Forthnet-1575C' [AC3]>
[ 7559.310257] wlan0: send auth to <MAC 'Forthnet-1575C' [AC3]> (try 1/3)
[ 7559.312812] wlan0: authenticated
[ 7559.315350] wlan0: associate with <MAC 'Forthnet-1575C' [AC3]> (try 1/3)
[ 7559.320093] wlan0: RX AssocResp from <MAC 'Forthnet-1575C' [AC3]> (capab=0x411 status=0 aid=1)
[ 7559.320672] wlan0: associated
[ 7576.535462] r8169 0000:03:00.0 eth0: link down
[ 7578.294846] r8169 0000:03:00.0 eth0: link up
[ 7605.768144] wlan0: deauthenticating from <MAC 'Forthnet-1575C' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)


########## wireless info END ############
```

---

### Post by Hadaka on 2016-04-01
Hi, from a working wired connection please open a terminal ctrl/alt/t then copy and paste..
*Remove the USB wifi unit.
```
sudo apt-get update
``````
sudo iw reg set GR
sudo sed -i 's/^REG.*=$/&GR/' /etc/default/crda
```
 then go here and follow these directions..
[http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
remove wired connection boot and test wireless
thanks.

---

### Post by wildmanne39 on 2016-04-01
Please use code tags by clicking on # at the top of the this window and placing it between the brackets when posting code.
Thanks

---

