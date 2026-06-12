---
title: "Wireless slow and choopy"
date: 2014-06-05
forum: Networking &amp; Wireless
---

### Post by G. Rodrigues on 2014-06-05
Asus M11AD, on Kubuntu 14.04 with an Asus 2T2R dual band wifi, network connection is either very choppy and slow or rightdown refuses to connect. The problem is *not* with the wireless setup itself, since I am typing this from a laptop with the Asus right next to me, also with Kubuntu 14.04, and everything is just fine.


The output from the wireless_script is:

```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


grodrigues 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty


CPU    : Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz
Memory : 7924 MB
Uptime : 10:58:51 up 20 min,  3 users,  load average: 0,06, 0,11, 0,13




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]
    Kernel driver in use: rtl8821ae
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
    Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 003 Device 005: ID 13d3:3414 IMC Networks 
Bus 003 Device 004: ID 0461:4de2 Primax Electronics, Ltd 
Bus 003 Device 003: ID 0461:4dbf Primax Electronics, Ltd 
Bus 003 Device 002: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8821ae             575923  0 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
mac80211              626489  1 rtl8821ae
cfg80211              484040  2 mac80211,rtl8821ae
mxm_wmi                13021  1 nouveau
video                  19476  2 nouveau,asus_wmi
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
eeepc_wmi     (1): hotplug_wireless=N
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8821ae     (4): fwlps=N | ips=N | swenc=N | swlps=N
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 eth0           | Wired       | r8169     | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | rtl8821ae | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>


    Eduardo:         Infra, <MAC C-04 Eduardo>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    MEO-565C03:      Infra, <MAC C-07 MEO-565C03>, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    CLIMEX-2:        Infra, <MAC C-06 CLIMEX-2>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    Thomson36DE88:   Infra, <MAC C-08 Thomson36DE88>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    MEO-E2CA34:      Infra, <MAC C-11 MEO-E2CA34>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    ZON-4D70:        Infra, <MAC C-NA ZON-4D70 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    ZON-C7B0:        Infra, <MAC C-09 ZON-C7B0>, Freq 2422 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    MEO-WiFi:        Infra, <MAC C-03 MEO-WiFi>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    MEO-WiFi:        Infra, <MAC C-05 MEO-WiFi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84
    MEO-WiFi:        Infra, <MAC C-01 MEO-WiFi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74
    FON_ZON_FREE_INTERNET: Infra, <MAC C-02 FON_ZON_FREE_INTERNET>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47
    ZON-7A70:        Infra, <MAC C-NA ZON-7A70 1>, Freq 2422 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    Vodafone-990DF3: Infra, <MAC C-NA Vodafone-990DF3 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC C-NA FON_ZON_FREE_INTERNET 3>, Freq 2422 MHz, Rate 54 Mb/s, Strength 57
    FON_ZON_FREE_INTERNET: Infra, <MAC C-NA FON_ZON_FREE_INTERNET 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 50
    FON_ZON_FREE_INTERNET: Infra, <MAC C-NA FON_ZON_FREE_INTERNET 6>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64
    FINEWARE:        Infra, <MAC C-NA FINEWARE 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 44 WPA
    FON_ZON_FREE_INTERNET: Infra, <MAC C-10 FON_ZON_FREE_INTERNET>, Freq 2422 MHz, Rate 54 Mb/s, Strength 64
    ZON-A680:        Infra, <MAC C-12 ZON-A680>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC C-NA FON_ZON_FREE_INTERNET 4>, Freq 2417 MHz, Rate 54 Mb/s, Strength 47
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------




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


ZON-A680             : ssid=ZON-A680 | permissions=user:goncalo:; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : pt_PT.UTF-8)
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)




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
          Channel 165 (5.825 GHz) - 11 (2.462 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 MEO-WiFi>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"MEO-WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b73ec9a10
                    Extra: Last beacon: 1924ms ago
          Cell 02 - Address: <MAC C-02 FON_ZON_FREE_INTERNET>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016772f39b36
                    Extra: Last beacon: 27532ms ago
          Cell 03 - Address: <MAC C-03 MEO-WiFi>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"MEO-WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000605229a6add
                    Extra: Last beacon: 1620ms ago
          Cell 04 - Address: <MAC C-04 Eduardo>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Eduardo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000605229a6f6b
                    Extra: Last beacon: 1620ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 MEO-WiFi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"MEO-WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013821fffa4b
                    Extra: Last beacon: 1588ms ago
          Cell 06 - Address: <MAC C-06 CLIMEX-2>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"CLIMEX-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000021d82e2e90cc
                    Extra: Last beacon: 1520ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 MEO-565C03>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"MEO-565C03"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b73ec9193
                    Extra: Last beacon: 1928ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 Thomson36DE88>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Thomson36DE88"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000138220186b8
                    Extra: Last beacon: 1488ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 ZON-C7B0>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ZON-C7B0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024ec75fb169
                    Extra: Last beacon: 1896ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 FON_ZON_FREE_INTERNET>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024ec75fbaab
                    Extra: Last beacon: 1896ms ago
          Cell 11 - Address: <MAC C-11 MEO-E2CA34>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"MEO-E2CA34"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d55d7434a9
                    Extra: Last beacon: 1892ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 ZON-A680>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"ZON-A680"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000167747bc152
                    Extra: Last beacon: 1832ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 MEO-WiFi>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:off
                    ESSID:"MEO-WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b5f7ddba1c5
                    Extra: Last beacon: 1728ms ago




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8821ae]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
srcversion:     EF86DC7E83D9B90E1277B0A
depends:        mac80211,cfg80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)


[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8821 (rtl8821ae)
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
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=1c0a1a41-c210-4295-8344-bf50653f84b5 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.582571] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.582769] audit: initializing netlink socket (disabled)
[    0.681428] wmi: Mapper loaded
[    0.689357] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    7.284921] asus_wmi: ASUS WMI generic driver loaded
[    7.286835] asus_wmi: Initialization: 0x0
[    7.286850] asus_wmi: BIOS WMI version: 0.9
[    7.286876] asus_wmi: SFUN value: 0x0
[    7.287081] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input8
[    7.287516] asus_wmi: Disabling ACPI video driver
[    7.302905] rtl8821ae: module is from the staging directory, the quality is unknown, you have been warned.
[    7.303555] rtl8821ae 0000:03:00.0: enabling device (0000 -> 0003)
[    7.303622] rtl8821ae-0:rtl_pci_probe():<0-0> mem mapped space: start: 0xf7200000 len:00004000 flags:00140204, after map:0xffffc90004e70000
[    7.303633] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> Pci Bridge Vendor is found index: 0
[    7.303635] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 3:0:0:10ec:0
[    7.303636] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:link_ctl_reg:amd 0:28:1:8086:40:40:0
[    7.303659] rtl8821ae-0:rtl8821ae_read_eeprom_info():<0-0> Boot from EFUSE
[    7.316585] rtl8821ae: 
[    7.316715] rtl8821ae-0:_rtl8821ae_read_adapter_info():<0-0> dev_addr: <MAC wlan0>
[    7.316717] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[    7.316719] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[    7.416284] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, antNum is 2
[    7.416287] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_exist is 1
[    7.416288] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_type is 7
[    7.416445] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[    7.416446] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[    7.429078] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    7.429561] rtlwifi: wireless switch is on
[    7.429576] rtl8821ae-0:rtl_pci_intr_mode_legacy():<0-0> Pin-based Interrupt Mode!
[   11.767159] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.617657] rtl8821ae-0:rtl_pci_start():<0-0>  rtl_pci_start 
[   13.623224] rtl8821ae-0:rtl8821ae_download_fw():<0-0> normal Firmware SIZE 29198 
[   13.623226] rtl8821ae-0:rtl8821ae_download_fw():<0-0> Firmware Version(18), Signature(0x2101),Size(32)
[   13.636306] rtl8821ae-0:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070604 .
[   13.665859] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 0] = 0x32343638
[   13.665861] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 1] = 0x36363838
[   13.665862] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 2] = 0x28303234
[   13.665863] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 3] = 0x34363838
[   13.665864] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 4] = 0x26283032
[   13.665865] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[   13.665866] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[   13.665867] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[   13.665868] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 1] = 0x34343636
[   13.665869] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 2] = 0x26283032
[   13.665870] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 3] = 0x32343636
[   13.665871] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 4] = 0x24262830
[   13.665872] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[   13.665873] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[   13.665874] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[   13.766403] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   13.766439] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[   13.766443] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[   13.766682] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 3e
[   13.766689] rtl8821ae-0:rtl_pci_start():<0-0> rtl_pci_start OK
[   13.767078] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.767311] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.422886] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   16.826532] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   38.620716] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   40.024347] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   71.607955] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   73.011585] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  114.600575] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  116.004182] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  167.586485] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  168.990092] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  230.569737] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  231.973383] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  293.552991] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  294.956636] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  334.358118] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  335.761742] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  341.380220] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  342.783919] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  348.402381] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  349.806046] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  355.424515] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  356.828175] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  359.539399] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  360.943082] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  362.530646] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  363.934283] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  385.528533] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  386.932123] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  418.515722] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  419.919401] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  461.508332] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  462.911973] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  514.490239] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  515.893882] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  577.477495] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  578.881116] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  640.456752] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  641.860386] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  695.877379] rtl8821ae-0:rtl_pci_start():<0-0>  rtl_pci_start 
[  695.882802] rtl8821ae-0:rtl8821ae_download_fw():<0-0> normal Firmware SIZE 29198 
[  695.882808] rtl8821ae-0:rtl8821ae_download_fw():<0-0> Firmware Version(18), Signature(0x2101),Size(32)
[  695.896714] rtl8821ae-0:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070604 .
[  695.926272] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 0] = 0x32343638
[  695.926274] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 1] = 0x36363838
[  695.926276] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 2] = 0x28303234
[  695.926277] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 3] = 0x34363838
[  695.926279] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 4] = 0x26283032
[  695.926281] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[  695.926282] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[  695.926284] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[  695.926285] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 1] = 0x34343636
[  695.926287] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 2] = 0x26283032
[  695.926288] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 3] = 0x32343636
[  695.926290] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 4] = 0x24262830
[  695.926292] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[  695.926294] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[  695.926295] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[  696.026823] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  696.026859] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[  696.026864] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  696.027105] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 3e
[  696.027112] rtl8821ae-0:rtl_pci_start():<0-0> rtl_pci_start OK
[  696.027522] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  696.661782] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  698.065444] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  698.681269] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  700.084903] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  719.439711] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  720.843335] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  737.042399] rtl8821ae-0:rtl_pci_start():<0-0>  rtl_pci_start 
[  737.047707] rtl8821ae-0:rtl8821ae_download_fw():<0-0> normal Firmware SIZE 29198 
[  737.047713] rtl8821ae-0:rtl8821ae_download_fw():<0-0> Firmware Version(18), Signature(0x2101),Size(32)
[  737.061403] rtl8821ae-0:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070604 .
[  737.091029] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 0] = 0x32343638
[  737.091036] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 1] = 0x36363838
[  737.091040] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 2] = 0x28303234
[  737.091045] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 3] = 0x34363838
[  737.091050] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 4] = 0x26283032
[  737.091054] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[  737.091059] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[  737.091063] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[  737.091068] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 1] = 0x34343636
[  737.091072] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 2] = 0x26283032
[  737.091077] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 3] = 0x32343636
[  737.091081] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 4] = 0x24262830
[  737.091086] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[  737.091090] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[  737.091095] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[  737.191760] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  737.191801] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[  737.191810] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  737.192063] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 3e
[  737.192074] rtl8821ae-0:rtl_pci_start():<0-0> rtl_pci_start OK
[  737.192565] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  737.834829] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  739.238502] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  739.854318] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  741.257955] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  761.428582] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  762.832230] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  774.229178] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  775.632799] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  775.634039] wlan0: authenticate with <MAC C-12 ZON-A680>
[  775.634371] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-12 ZON-A680>
[  775.634494] wlan0: direct probe to <MAC C-12 ZON-A680> (try 1/3)
[  775.836717] wlan0: direct probe to <MAC C-12 ZON-A680> (try 2/3)
[  776.040692] wlan0: direct probe to <MAC C-12 ZON-A680> (try 3/3)
[  776.244639] wlan0: authentication with <MAC C-12 ZON-A680> timed out
[  776.248810] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  776.964452] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  778.368058] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  783.990583] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  785.394216] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  785.395579] wlan0: authenticate with <MAC C-12 ZON-A680>
[  785.395910] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-12 ZON-A680>
[  785.396027] wlan0: direct probe to <MAC C-12 ZON-A680> (try 1/3)
[  785.598115] wlan0: direct probe to <MAC C-12 ZON-A680> (try 2/3)
[  785.802094] wlan0: direct probe to <MAC C-12 ZON-A680> (try 3/3)
[  786.006038] wlan0: authentication with <MAC C-12 ZON-A680> timed out
[  786.010234] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  787.125749] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  788.529394] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  788.530538] wlan0: authenticate with <MAC C-12 ZON-A680>
[  788.530863] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-12 ZON-A680>
[  788.530982] wlan0: direct probe to <MAC C-12 ZON-A680> (try 1/3)
[  788.733318] wlan0: direct probe to <MAC C-12 ZON-A680> (try 2/3)
[  788.937261] wlan0: direct probe to <MAC C-12 ZON-A680> (try 3/3)
[  789.141206] wlan0: authentication with <MAC C-12 ZON-A680> timed out
[  789.145360] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  790.760779] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  792.164381] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  797.782889] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  799.186557] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  802.413681] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  803.817286] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  825.407547] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  826.811210] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  858.402772] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  859.806437] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  901.391355] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  902.794959] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  954.377276] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  955.780922] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1017.356532] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1018.760178] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1055.042509] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1056.446152] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1056.447677] wlan0: authenticate with <MAC C-12 ZON-A680>
[ 1056.448013] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-12 ZON-A680>
[ 1056.448127] wlan0: direct probe to <MAC C-12 ZON-A680> (try 1/3)
[ 1056.650039] wlan0: direct probe to <MAC C-12 ZON-A680> (try 2/3)
[ 1056.853984] wlan0: direct probe to <MAC C-12 ZON-A680> (try 3/3)
[ 1057.057930] wlan0: authentication with <MAC C-12 ZON-A680> timed out
[ 1057.066073] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1062.684453] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1064.088118] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1069.702614] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1071.106201] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1071.106991] wlan0: authenticate with <MAC C-12 ZON-A680>
[ 1071.107283] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-12 ZON-A680>
[ 1071.107337] wlan0: direct probe to <MAC C-12 ZON-A680> (try 1/3)
[ 1071.310119] wlan0: direct probe to <MAC C-12 ZON-A680> (try 2/3)
[ 1071.514081] wlan0: direct probe to <MAC C-12 ZON-A680> (try 3/3)
[ 1071.718033] wlan0: authentication with <MAC C-12 ZON-A680> timed out
[ 1071.722250] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1080.351779] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1081.755369] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1083.338985] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1084.742604] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1106.336871] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1107.740460] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1139.328098] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1140.731748] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1182.316668] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1183.720314] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1235.298579] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1236.702185] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1261.015744] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1262.419387] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G


    ======== Done ========
```


To add insult to injury, I cannot update. If I do (and I did, waiting for a long time for the download to finish) besides a whole number of packages, the kernel updates from 3.13.0-24 to 3.13.0-27 and *then* it refuses to load Kubuntu, with a black screen full of text, the last line being:


x86_64_start_kernel +0x143/0x152


I have just reinstalled Kubuntu afresh from the live usb so back to being able to boot kubuntu. So I suppose this is two bugs in one; but since without decent wifi, no chance I am updating my desktop, I opted for posting the problem in the wireless section.

edit: I cannot connect at all now, with the network manager saying the network not found. I have also rerun wireless_script, which this time seems to report much more info, e.g. iwlist scan is not empty. I have just replaced the original by this one. I have also noticed that a new kernel 3.13.0-29 is available in the updates, but since I have no network access in the desktop no chance to try it.

Any help is much appreciated, thanks in advance.

---

### Post by varunendra on 2014-06-06
> **G. Rodrigues said:**
> ```
[    7.302905] rtl8821ae: module is from the staging directory, **the quality is unknown, you have been warned.**
```

Did you notice that innocent little warning? These drivers tend to act funny at times, not much surprise there. I don't have experience with this driver, so can't say how much we can/should expect from it in terms of performance. Let's see what we can try..

The access-point it is trying to connect to is using WPA/WPA2 mixed mode with **TKIP** - bad if not too bad! Please change it (in the router) to pure WPA2-PSK with AES (CCMP). Keep this as suggested even if it doesn't seem to help immediately.

Also try changing the channel to 1 or 11. Currently it is using channel 6 which is okay, but 1 or 11 usually offer better signal quality.

Another thing to check/change is frequency band. Is the router using 'Auto' or '2.4/5 GHz mixed mode'? If yes, I suggest trying 2.4 GHz alone, then 5 GHz alone if 2.4 GHz doesn't help. Seeing the congestion, 5 GHz may be better, but many Linux drivers simply don't like it, so try good old 2.4 GHz first (of course if the router has the dual band option).

Reboot the router after saving any changes.

In Ubuntu, try -
```
sudo modprobe -rv rtl8821ae
sudo modprobe -v rtl8821ae swenc=Y
```
This would be a temporary change that would be lost at next boot. If it helps, can be made permanent. The other driver parameters look okay, although they don't seem to be at defaults suggested by 'modinfo'. Did you manually load some parameters before running the script?

Oh, and unless you are really using IPv6, try setting it to "Ignore" in Network Manager, or completely disable it following this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

---

### Post by G. Rodrigues on 2014-06-06
First, thanks a lot for the help.

> Did you notice that innocent little warning?

Was just about to edit my post to comment on just that. With a little bit of research, it turns out the driver for the rtl8821ae is still recent (only committed in 3.13.0-16), pulled off from staging, and expected to be final only in 3.15. IOW, decent, working drivers can only be expected in a few more kernel iterations.

In the meantime, I dug up an old but still working wireless usb adapter. A lucky break (!) allowed me to connect to the internet, something I had not managed to do in a long while. So I installed linux-firmware-nonfree via apt-get (it may be possible to do it also via the additional drivers), rebooted and connected via the usb interface. Still somewhat choppy and slow, but *considerably* more stable. 

So what I am going to do is try your suggestions and then report back here (just in case someone may be having the same problems) and then, maybe whether it works or not, mark the thread as [SOLVED] and just resign myself to wait for a working driver while falling back to the usb adaptor.

Now, on to the next problem... Updating to 3.13.0-29 still leaves me with an unusable system, but now that I can get internet access I will open a new thread in the proper subsection.

---

### Post by varunendra on 2014-06-06
Just a comment..
> **G. Rodrigues said:**
> ..So I installed linux-firmware-nonfree via apt-get (it **may be possible to do it also via the [COLOR="#FF0000"]additional drivers[/COLOR]**)
Nope, the "Additional Drivers" offering breaks what "linux-firmware-nonfree" fixes. The firmware package is meant for drivers that are natively available, just need a proprietary firmware, while the "Additional Drivers" offerings are drivers (proprietary) themselves, that are simply alternatives of the native ones (if native drivers exist for the device in question). One has to disable the other in order to work without conflicts. :)

---

### Post by G. Rodrigues on 2014-06-07
Starting at the end:

> The other driver parameters look okay, although they don't seem to be at defaults suggested by 'modinfo'. Did you manually load some parameters before running the script?

No, I have not changed anything.

(1) About the changes to the router: not implemented yet. I have to jump through some hoops to get them in and will only be able to do it in a week or so.

Either way the problems cannot be only in the router (though they may be exacerbated by it), because I can access the internet just fine from my older laptop, located less than a meter from the desktop, which also has Kubuntu Trusty on it (upgraded, not a fresh install). Which reminds me: maybe I should compare the output of wireless_script for the two computers; maybe the laptop has the configuration pegged down just right.

(2) Both modprobe commands and setting IPv6 to ignore did not seem to make any notable difference.

Also, my enthusiasm with falling back to my old usb adapter has cooled down somewhat as the connection, although a bit more stable, is also slow and choppy and tends to drop a lot. 

I will mark the thread as [SOLVED], not because it is really solved but because I suspect the solution is bound to solve some other problems first like the one with the updated kernel mentioned above; if I cannot get things better I may come back here for some more advice.

Once again, thanks for all the help.

---

