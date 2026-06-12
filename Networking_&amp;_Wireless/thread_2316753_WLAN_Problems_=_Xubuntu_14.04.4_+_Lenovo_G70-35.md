---
title: "WLAN Problems = Xubuntu 14.04.4 + Lenovo G70-35"
date: 2016-03-10
forum: Networking &amp; Wireless
---

### Post by Sascha_Ansorge on 2016-03-10
Hi dear ubuntu-community,

I am totally new to Linux and its derivates.

As you can see in the topic I got a fresh Lenovo G70-35 only with FreeDos preinstalled. I installed Xubuntu-14.04.4-desktop-AMD64bit via Live-CD and eradecated FreeDos in the process (Bwuahahahaaa :D).

First: I am already a fan of Linux, cause the easiest OS-Installation in my whole live.

Second: My early enthusiasm was killed by my WLAN-Connection that is passing out after a view minutes in active OS (Bwoohoohoohooo :(). After a restart I got WLAN-Connectivity again for some minutes until its passing out again.

I used this line: 
lspci | grep Wireless

The answer was:

**01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter**

So... what to do now?

I would appreciate an step by step explanation ;).


Greetings


Sascha

PS: I have now read the sticky and made the update without any change in my connection problem.

sudo apt-get update
sudo apt-get dist-upgrade

After that trial failed I started the script in the sticky.

```



########## wireless info START ##########

Report from: 12 Mar 2016 14:59 CET +0100

Booted last: 12 Mar 2016 14:55 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-30-generic #36~14.04.1-Ubuntu SMP Fri Feb 26 18:49:23 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3812]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 5986:014f Acer, Inc 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be              90112  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              729088  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              540672  2 mac80211,rtlwifi
ideapad_laptop         24576  0 
sparse_keymap          16384  1 ideapad_laptop
video                  40960  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2001:4c50:d4a:d00:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2001:4c50:d4a:d00:b825:5fa:e376:f632/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26399625 (26.3 MB)  TX bytes:1207686 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          inet6 addr: 2001:4c50:d4a:d00:<IP6 'wlan0' [IF]>/64 Scope:Global
          inet6 addr: 2001:4c50:d4a:d00:8075:fbcb:9c30:7fc2/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33732 (33.7 KB)  TX bytes:24885 (24.8 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Tech_D0058443"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Tech_D0058443' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search cm.cablesurf.de

##### network managers ##################

Installed:

    NetworkManager

Running:

root       993     1  0 14:55 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             195.234.128.9
    DNS:             195.234.128.16

- Device: wlan0  [Tech_D0058443] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    EasyBox-609332:  Infra, <MAC 'EasyBox-609332' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    FRITZ!Box 7362 SL: Infra, <MAC 'FRITZ!Box 7362 SL' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    WLAN:            Infra, <MAC 'WLAN' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Gartenlaube26:   Infra, <MAC 'Gartenlaube26' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    KaterTom:        Infra, <MAC 'KaterTom' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    EasyBox-C7DA50:  Infra, <MAC 'EasyBox-C7DA50' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Motorola:        Infra, <MAC 'Motorola' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WEP
    *Tech_D0058443:  Infra, <MAC 'Tech_D0058443' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 86 WPA WPA2
    Tilla:           Infra, <MAC 'Tilla' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2
    FRITZ!Box 7412:  Infra, <MAC 'FRITZ!Box 7412' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2

  IPv4 Settings:
    Address:         192.168.0.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             195.234.128.9
    DNS:             195.234.128.16

  IPv6 Settings:
    Address:         2001:4c50:d4a:d00:<IP6 'wlan0' [IF]>
    Prefix:          128
    Gateway:         ::

    Address:         2001:4c50:d4a:d00:8075:fbcb:9c30:7fc2
    Prefix:          64
    Gateway:         ::

    Address:         2001:4c50:d4a:d00:<IP6 'wlan0' [IF]>
    Prefix:          64
    Gateway:         ::

    Address:         fe80::<IP6 'wlan0' [IF]>
    Prefix:          64
    Gateway:         ::

    DNS:             2001:4c50:6:4000::12
    DNS:             2001:4c50:6:4000::16

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

[[/etc/NetworkManager/system-connections/Tech_D0058443]] (600 root)
[connection] id=Tech_D0058443 | type=802-11-wireless
[802-11-wireless] ssid=Tech_D0058443 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

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

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Tech_D0058443' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Tech_D0058443"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000251d097423
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'EasyBox-609332' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-609332"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004bb1905a598
                    Extra: Last beacon: 76ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: <MAC 'WLAN' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"WLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004b5827f8180
                    Extra: Last beacon: 204ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Motorola' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Motorola"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c6d99b385
                    Extra: Last beacon: 76ms ago
          Cell 05 - Address: <MAC 'FRITZ!Box 7412' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7412"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000103fad8a180
                    Extra: Last beacon: 816ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Gartenlaube26' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Gartenlaube26"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000540aa92237
                    Extra: Last beacon: 812ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Tilla' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Tilla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006d66a8e2005
                    Extra: Last beacon: 464ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0EB6BE33DFAD6AEFD4D63AE
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
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
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2E1C688267DE11E1F26A728
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     F4CACC5FCAEBE7C22930A24
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6C:36:8A:BF:94:3C:D4:16:83:EB:2A:51:99:BF:B9:B4:01:ED:5A:B5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

##### dmesg #############################

[   40.939171] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   40.977715] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   40.978242] rtlwifi: rtlwifi: wireless switch is on
[   45.330020] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.376236] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   45.376313] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.899364] wlan0: authenticate with <MAC 'Tech_D0058443' [AC1]>
[   46.910870] wlan0: send auth to <MAC 'Tech_D0058443' [AC1]> (try 1/3)
[   46.914169] wlan0: authenticated
[   46.918299] wlan0: associate with <MAC 'Tech_D0058443' [AC1]> (try 1/3)
[   46.923037] wlan0: RX AssocResp from <MAC 'Tech_D0058443' [AC1]> (capab=0x411 status=0 aid=1)
[   46.923906] wlan0: associated
[   46.923926] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.286045] r8169 0000:02:00.0 eth0: link up
[   48.286068] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

I am now using the wired ethernet adapter and it seems to work fine, nevertheless do I need the WLAN-connectivity

I guess this user got the same problem like me:

[http://ubuntuforums.org/showthread.php?t=2316199&highlight=Realtek+Semiconductor+Co.%2C+Ltd.+RTL8723BE+PCIe+Wireless+Network+Adapter](http://ubuntuforums.org/showthread.php?t=2316199&highlight=Realtek+Semiconductor+Co.%2C+Ltd.+RTL8723BE+PCIe+Wireless+Network+Adapter)

---

### Post by howefield on 2016-03-10
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by Sascha_Ansorge on 2016-03-13
It seems I found the solution in the forum :D.

```

echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf


```

Worked out fine until now. Here is the Link: [URL="http://ubuntuforums.org/showthread.php?t=2243978"]http://ubuntuforums.org/showthread.php?t=2243978
[/URL]
Considering the problem as solved :KS.

---

