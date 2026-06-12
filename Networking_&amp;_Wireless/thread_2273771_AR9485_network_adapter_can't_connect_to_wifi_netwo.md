---
title: "AR9485 network adapter can't connect to wifi networks with passwords"
date: 2015-04-15
forum: Networking &amp; Wireless
---

### Post by adam141 on 2015-04-15
Hi,

My asus laptop is running ubuntu 14.04 and can't connect to protected wireless networks. I can't open the 'settings' dialog in the network manager UI, and I don't see a network indication in the ubuntu top bar either :(

This is the output of the wireless_script
```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


eliq-ubuntu 3.13.0-49-generic x86_64,  Ubuntu 14.04.2 LTS, trusty


CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 3837 MB
Uptime : 20:24:43 up 23 min,  2 users,  load average: 0.07, 0.12, 0.15




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2126]
    Kernel driver in use: ath9k




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 03eb:8810 Atmel Corp. 
Bus 001 Device 003: ID 09da:054f A4 Tech Co., Ltd 
Bus 001 Device 008: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 13d3:5195 IMC Networks 
Bus 002 Device 003: ID 13d3:3402 IMC Networks 
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface               Soft blocked  Hard blocked
0: hci0: Bluetooth                no            no
1: phy0: Wireless LAN             no            no
2: asus-wlan: Wireless LAN        no            no
3: asus-bluetooth: Bluetooth      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): 
ath9k         (5): 
cfg80211      (2): 
mac80211      (5): 
video         (3): 
wmi           (2): 




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
====================o=============o========o======  =======o=========o===========o==============o=====  ======
 Interface & ID     | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
====================o=============o========o======  =======o=========o===========o==============o=====  ======
 wlan0  [Frederick] | 802.11 WiFi | ath9k  | connected   | yes     | 1 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>


    Karen2:          Infra, <MAC C-04 Karen2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 95 WPA2
    Karen2_2GEXT:    Infra, <MAC C-09 Karen2_2GEXT>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    ShepherdEnt:     Infra, <MAC C-01 ShepherdEnt>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    xfinitywifi:     Infra, <MAC C-NA xfinitywifi 2>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67
    BaseCamp:        Infra, <MAC C-NA BaseCamp 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Chomowicz:       Infra, <MAC C-NA Chomowicz 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Pisica:          Infra, <MAC C-10 Pisica>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2
    Manning@Marshal: Infra, <MAC C-05 Manning@Marshal>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2
    DOYLELOVE-2.4:   Infra, <MAC C-03 DOYLELOVE-2.4>, Freq 2437 MHz, Rate 54 Mb/s, Strength 99 WPA WPA2
    HOME-5F22:       Infra, <MAC C-NA HOME-5F22 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    *Frederick:      Infra, <MAC C-NA *Frederick 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    xfinitywifi:     Infra, <MAC C-NA xfinitywifi 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    xfinitywifi:     Infra, <MAC C-NA xfinitywifi 3>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    Marshall38Manning: Infra, <MAC C-06 Marshall38Manning>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    A Van Down By The River: Infra, <MAC C-07 A Van Down By The River>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2


    Address:         192.168.3.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.3.1
    DNS:             192.168.3.1
--------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth0               | Wired       | r8169  | unavailable | no      |           |              | <MAC eth0>
--------------------+-------------+--------+-------------+---------+-----------+--------------+-----------




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


DOYLELOVE-2.4        : ssid=DOYLELOVE-2.4 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Frederick            : ssid=Frederick | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
GoogleGuestPSK       : ssid=GoogleGuestPSK | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
LeahGoldberg         : ssid=LeahGoldberg | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
LeahGoldberg         : ssid=LeahGoldberg | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
LeahGoldberg         : ssid=LeahGoldberg | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
LeahGoldberg         : ssid=LeahGoldberg | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
naama                : ssid=naama | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
rsipvision           : ssid=rsipvision | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
tele2-FB08           : ssid=tele2-FB08 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
UPC2257657           : ssid=UPC2257657 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search hsd1.or.comcast.net




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.3.1     0.0.0.0         UG    0      0        0 wlan0
192.168.3.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.3.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms




--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.020/0.037/0.055/0.018 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : he_IL.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 ShepherdEnt>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ShepherdEnt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d52729133c
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000204af27aa5b
                    Extra: Last beacon: 668ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 DOYLELOVE-2.4>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"DOYLELOVE-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000204af27c739
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Karen2>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Karen2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001921d506d8e
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Manning@Marshal>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Manning@Marshal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014b12005142
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 Marshall38Manning>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Marshall38Manning"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004e708dc7a82
                    Extra: Last beacon: 12952ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 A Van Down By The River>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"A Van Down By The River"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d76a4a17ab
                    Extra: Last beacon: 7536ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 >
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d76a0d2122
                    Extra: Last beacon: 11532ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 Karen2_2GEXT>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Karen2_2GEXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001921d500079
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 Pisica>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Pisica"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001a6ea930
                    Extra: Last beacon: 708ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 >
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004e7098d0ab6
                    Extra: Last beacon: 1380ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[asus_nb_wmi]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
parm:           wapf:WAPF value (uint)


[asus_wmi]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video


[ath9k]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     274594FBD61F5DF88102A4C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     65C14EF588BF1A68181643C
depends:        ath


[ath]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/mac80211/mac80211.ko
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/wireless/cfg80211.ko
srcversion:     176113E009F723E69BE9BAB
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/acpi/video.ko
srcversion:     FD364E86295EDCA7831C8FB
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
asus.conf         : options asus_nb_wmi wapf=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-49-generic.efi.signed root=UUID=9de7096d-92bf-4c06-b519-7ba40ace689a ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.693163] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.693489] audit: initializing netlink socket (disabled)
[    0.846401] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.905111] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f01)
[   12.628936] wmi: Mapper loaded
[   12.738773] ath: phy0: Set parameters for CUS198
[   12.738777] ath: phy0: Set BT/WLAN RX diversity capability
[   12.744595] ath: phy0: Enable LNA combining
[   12.745761] ath: EEPROM regdomain: 0x60
[   12.745762] ath: EEPROM indicates we should expect a direct regpair map
[   12.745764] ath: Country alpha2 being used: 00
[   12.745764] ath: Regpair used: 0x60
[   12.805933] asus_wmi: ASUS WMI generic driver loaded
[   12.807512] asus_wmi: Initialization: 0x1
[   12.807558] asus_wmi: BIOS WMI version: 7.9
[   12.807611] asus_wmi: SFUN value: 0x4a0877
[   12.808893] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input17
[   12.820084] asus_wmi: Backlight controlled by ACPI video driver
[   29.500138] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.095755] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.098692] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.187085] wlan0: authenticate with <MAC C-NA *Frederick 1>
[   32.204867] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[   32.217174] wlan0: authenticated
[   32.221004] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[   32.232650] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[   32.232696] wlan0: associated
[   32.232706] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.889362] wlan0: authenticate with <MAC C-NA *Frederick 1>
[   46.912691] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[   46.928925] wlan0: authenticated
[   46.932868] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[   46.943776] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[   46.943821] wlan0: associated
[   74.835840] wlan0: deauthenticating from <MAC C-NA *Frederick 1> by local choice (reason=3)
[   78.919934] wlan0: authenticate with <MAC C-NA *Frederick 1>
[   78.943003] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[   78.960942] wlan0: authenticated
[   78.963012] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[   78.972077] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[   78.972125] wlan0: associated
[   78.972656] wlan0: deauthenticating from <MAC C-NA *Frederick 1> by local choice (reason=2)
[   78.981961] wlan0: authenticate with <MAC C-NA *Frederick 1>
[   78.998709] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[   79.012891] wlan0: authenticated
[   79.015019] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[   79.023763] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[   79.023804] wlan0: associated
[   86.907890] wlan0: deauthenticating from <MAC C-NA *Frederick 1> by local choice (reason=3)
[   89.963834] wlan0: authenticate with <MAC C-NA *Frederick 1>
[   89.981154] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[   90.014461] wlan0: authenticated
[   90.016883] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[   90.024994] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[   90.025038] wlan0: associated
[  388.675664] wlan0: authenticate with <MAC C-NA *Frederick 1>
[  388.701713] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[  388.708806] wlan0: send auth to <MAC C-NA *Frederick 1> (try 2/3)
[  388.720602] wlan0: authenticated
[  388.722632] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[  388.766582] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[  388.766652] wlan0: associated
[  392.686113] wlan0: authenticate with <MAC C-NA *Frederick 1>
[  392.708589] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[  392.713255] wlan0: authenticated
[  392.716386] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[  392.734279] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[  392.734343] wlan0: associated
[  776.480350] wlan0: authenticate with <MAC C-NA *Frederick 1>
[  776.502739] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[  776.644709] wlan0: send auth to <MAC C-NA *Frederick 1> (try 2/3)
[  776.762447] wlan0: send auth to <MAC C-NA *Frederick 1> (try 3/3)
[  776.824411] wlan0: authentication with <MAC C-NA *Frederick 1> timed out
[  790.818426] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  894.480635] wlan0: authenticate with <MAC C-NA *Frederick 1>
[  894.497708] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[  894.530895] wlan0: authenticated
[  894.533095] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[  894.542119] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[  894.542161] wlan0: associated
[  894.542169] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1131.234905] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1131.257710] wlan0: direct probe to <MAC C-NA *Frederick 1> (try 1/3)
[ 1131.461295] wlan0: send auth to <MAC C-NA *Frederick 1> (try 2/3)
[ 1131.463271] wlan0: authenticated
[ 1131.465279] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1131.498609] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1131.498661] wlan0: associated
[ 1169.257132] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1169.280282] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1169.282240] wlan0: authenticated
[ 1169.284133] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1169.326928] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1169.327012] wlan0: associated
[ 1182.242520] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1182.265055] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1182.267699] wlan0: authenticated
[ 1182.268981] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1182.279698] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1182.279768] wlan0: associated
[ 1190.246043] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1190.268664] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1190.270626] wlan0: authenticated
[ 1190.272522] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1190.349112] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1190.349205] wlan0: associated
[ 1199.232683] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1199.258323] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1199.275080] wlan0: authenticated
[ 1199.275441] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1199.351853] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1199.351923] wlan0: associated
[ 1205.233574] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1205.256333] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1205.266105] wlan0: authenticated
[ 1205.268187] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1205.288726] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1205.288796] wlan0: associated
[ 1212.237610] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1212.260531] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1212.267017] wlan0: authenticated
[ 1212.268279] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1212.295727] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1212.295772] wlan0: associated
[ 1215.228430] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1215.250691] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1215.422699] wlan0: authenticated
[ 1215.426547] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1215.440225] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1215.440299] wlan0: associated
[ 1312.133891] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1312.156873] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1312.183428] wlan0: authenticated
[ 1312.184695] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1312.205291] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1312.205343] wlan0: associated
[ 1409.120344] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1409.143032] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1409.152906] wlan0: authenticated
[ 1409.154704] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1409.173858] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1409.173927] wlan0: associated
[ 1411.115968] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1411.137673] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1411.171118] wlan0: authenticated
[ 1411.173594] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1411.201338] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1411.201402] wlan0: associated
[ 1413.114140] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1413.136666] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1413.146643] wlan0: authenticated
[ 1413.148497] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1413.214816] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1413.214887] wlan0: associated
[ 1415.120620] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1415.143539] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1415.156435] wlan0: authenticated
[ 1415.159369] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1415.400206] wlan0: associate with <MAC C-NA *Frederick 1> (try 2/3)
[ 1415.410963] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=1 aid=8)
[ 1415.410973] wlan0: <MAC C-NA *Frederick 1> denied association (code=1)
[ 1415.422735] wlan0: deauthenticating from <MAC C-NA *Frederick 1> by local choice (reason=3)
[ 1416.879427] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1416.902507] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1416.930447] wlan0: authenticated
[ 1416.934331] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1417.004206] wlan0: RX AssocResp from <MAC C-NA *Frederick 1> (capab=0x401 status=0 aid=8)
[ 1417.004288] wlan0: associated
[ 1419.118687] wlan0: authenticate with <MAC C-NA *Frederick 1>
[ 1419.141284] wlan0: send auth to <MAC C-NA *Frederick 1> (try 1/3)
[ 1419.147369] wlan0: authenticated
[ 1419.149134] wlan0: associate with <MAC C-NA *Frederick 1> (try 1/3)
[ 1419.390560] wlan0: associate with <MAC C-NA *Frederick 1> (try 2/3)
[ 1419.538729] wlan0: associate with <MAC C-NA *Frederick 1> (try 3/3)
[ 1419.657951] wlan0: association with <MAC C-NA *Frederick 1> timed out


    ======== Done ========



```


Please help me, it's frustrating...

Thanks,
Adam

---

