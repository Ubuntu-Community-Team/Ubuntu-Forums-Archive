---
title: "Intel Wireless 7260"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by rafael10 on 2014-09-07
Hello Ive been having serous connection issues on ubuntu ill post my wirless script if anyone has any idea please help me. ```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Alpha 3.15.0-031500rc3-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7868 MB
Uptime : 21:20:07 up 1 day,  5:25,  3 users,  load average: 0.74, 1.42, 1.84




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
    Kernel driver in use: iwlwifi




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 010: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 018: ID 8087:07dc Intel Corp. 
Bus 001 Device 020: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abgn  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC C-01 belkin.986>   
          Bit Rate=150 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:81   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      yes           no
2: phy0: Wireless LAN             no            no
5: hci0: Bluetooth                yes           no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwlmvm                216368  0 
mac80211              663788  1 iwlmvm
iwlwifi               181776  1 iwlmvm
asus_nb_wmi            16990  0 
asus_wmi               24697  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
cfg80211              509833  3 iwlwifi,mac80211,iwlmvm
wmi                    19379  1 asus_wmi
video                  19932  2 i915,asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=1
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=1 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=====================o=============o=========o====  =========o=========o===========o==============o===  ========
 Interface & ID      | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
=====================o=============o=========o====  =========o=========o===========o==============o===  ========
 wlan0  [belkin.986] | 802.11 WiFi | iwlwifi | connected   | yes     | 135 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>


    2WIRE951:        Infra, <MAC C-04 2WIRE951>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    NETGEAR95:       Infra, <MAC C-NA NETGEAR95 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    2WIRE000:        Infra, <MAC C-NA 2WIRE000 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    *belkin.986:     Infra, <MAC C-01 belkin.986>, Freq 2457 MHz, Rate 54 Mb/s, Strength 61 WPA2
    NETGEAR63:       Infra, <MAC C-02 NETGEAR63>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2
    MyCharterWiFi3f-2G: Infra, <MAC C-03 MyCharterWiFi3f-2G>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    MyCharterWiFi71-2G: Infra, <MAC C-NA MyCharterWiFi71-2G 1>, Freq 2422 MHz, Rate 54 Mb/s, Strength 37 WPA2
    2WIRE132:        Infra, <MAC C-05 2WIRE132>, Freq 2457 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2


    Address:         192.168.2.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
---------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169   | unavailable | no      |           |              | <MAC eth0>
---------------------+-------------+---------+-------------+---------+-----------+--------------+-----------




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


belkin.986           : ssid=belkin.986 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search Belkin




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.233/1.233/1.234/0.035 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.020/0.020/0.021/0.004 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)


          Current Frequency:2.457 GHz (Channel 10)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 belkin.986>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"belkin.986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000008fedfd5
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 NETGEAR63>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000570340c3f79
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 MyCharterWiFi3f-2G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"MyCharterWiFi3f-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001fbfbaa2183
                    Extra: Last beacon: 19032ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 2WIRE951>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"2WIRE951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b69085493
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 2WIRE132>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"2WIRE132"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000052003181
                    Extra: Last beacon: 18624ms ago
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




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[iwlmvm]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     7F619E415D8ECAAAD38E153
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/net/mac80211/mac80211.ko
srcversion:     AE7FF15CC48CEBF86450AA1
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-8.ucode
firmware:       iwlwifi-3160-8.ucode
firmware:       iwlwifi-7260-8.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     7EEF6B6542F122FA91624B7
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[asus_nb_wmi]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
parm:           wapf:WAPF value (uint)


[asus_wmi]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     F1B598E231F902960383641
depends:        sparse-keymap,wmi,video


[cfg80211]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/net/wireless/cfg80211.ko
srcversion:     EE81A925F8AD66571D5F75D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/acpi/video.ko
srcversion:     D25687678246FBE9023F1F2
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modprobe.d]
iwlmvm.conf       : options iwlmvm power_scheme=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi bt_coex_active=N swcrypto=1
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/power.d/wireless] [executable]
iwconfig wlan0 power off




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.15.0-031500rc3-generic root=UUID=1bac92c1-18ae-4b7a-8223-d2adad876efd ro quiet splash




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.071079] Initializing cgroup subsys net_cls
[    1.586559] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.587314] audit: initializing netlink subsys (disabled)
[    1.865559] wmi: Mapper loaded
[    1.883628] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.854533] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[    9.423002] asus_wmi: ASUS WMI generic driver loaded
[    9.434406] asus_wmi: Initialization: 0x1
[    9.434552] asus_wmi: BIOS WMI version: 7.9
[    9.434709] asus_wmi: SFUN value: 0x4a0877
[    9.436984] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input15
[    9.453275] asus_wmi: Backlight controlled by ACPI video driver
[    9.464574] iwlwifi 0000:03:00.0: irq 64 for MSI/MSI-X
[    9.831813] iwlwifi 0000:03:00.0: loaded firmware version 23.214.9.0 op_mode iwlmvm
[   10.255981] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   10.256044] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   10.256268] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   10.557847] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   16.336688] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.827893] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   19.828221] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   19.840122] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.365010] wlan0: authenticate with <MAC C-01 belkin.986>
[   23.366344] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   23.368072] wlan0: authenticated
[   23.371193] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   23.375082] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[   23.377640] wlan0: associated
[   23.377702] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.706993] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[   32.718409] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   32.718747] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   32.730276] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.636355] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   33.636692] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   33.647975] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.705842] wlan0: authenticate with <MAC C-01 belkin.986>
[   36.706816] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   36.708582] wlan0: authenticated
[   36.711769] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   36.715656] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[   36.718378] wlan0: associated
[   36.718422] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13730.520315] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[13731.836245] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13731.836563] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13731.848704] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13731.859752] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13731.860071] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13731.870886] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13732.271065] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13732.271389] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13732.282957] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13735.225342] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13735.225570] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13737.537586] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[13737.666025] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[13742.794792] wlan0: authenticate with <MAC C-01 belkin.986>
[13742.796284] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[13742.798031] wlan0: authenticated
[13742.798407] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[13742.805092] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[13742.808277] wlan0: associated
[13742.808371] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13743.111075] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[13743.126801] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13743.127040] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13743.139133] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13743.582011] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13743.582240] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13743.593846] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13746.666825] wlan0: authenticate with <MAC C-01 belkin.986>
[13746.668433] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[13746.671797] wlan0: authenticated
[13746.672438] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[13746.679991] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[13746.682383] wlan0: associated
[13746.682454] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[29466.114852] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[29467.238280] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29467.238494] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29467.249748] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29467.262816] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29467.263058] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29467.274185] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29468.066895] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29468.067129] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29468.078714] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29470.262073] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[29470.336624] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29470.336847] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29471.702781] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[29471.835697] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[29477.910569] wlan0: authenticate with <MAC C-01 belkin.986>
[29477.913444] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[29477.915468] wlan0: authenticated
[29477.916482] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[29477.920325] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[29477.922743] wlan0: associated
[29477.922774] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[29478.186353] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[29478.201150] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29478.201481] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29478.212195] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29478.586730] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29478.587057] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29478.597837] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29481.650576] wlan0: authenticate with <MAC C-01 belkin.986>
[29481.652070] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[29481.654473] wlan0: authenticated
[29481.658166] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[29481.662026] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[29481.672071] wlan0: associated
[29481.672103] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[29866.621443] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[29867.317505] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29867.317719] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29867.328782] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29867.335574] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29867.335789] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29867.346895] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29867.795987] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29867.796205] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29867.806744] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29870.174340] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[29871.181519] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29871.181734] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29871.609292] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[29871.727949] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[29877.653526] wlan0: authenticate with <MAC C-01 belkin.986>
[29877.654738] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[29877.668542] wlan0: authenticated
[29877.674528] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[29877.700125] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[29877.701188] wlan0: associated
[29877.701224] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[29877.879218] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[29877.880182] iwlwifi 0000:03:00.0: Drained sta 0, but it is internal?
[29877.887205] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29877.887535] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29877.898537] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29878.373326] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29878.373638] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[29878.384523] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29881.259615] wlan0: authenticate with <MAC C-01 belkin.986>
[29881.261048] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[29881.263344] wlan0: authenticated
[29881.263902] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[29881.267758] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[29881.270209] wlan0: associated
[29881.270234] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[35522.630320] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[35525.599127] wlan0: authenticate with <MAC C-01 belkin.986>
[35525.600447] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[35525.604691] wlan0: authenticated
[35525.606464] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[35525.739200] wlan0: associate with <MAC C-01 belkin.986> (try 2/3)
[35525.743615] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[35525.746051] wlan0: associated
[35722.929737] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[35722.929741] iwlwifi 0000:03:00.0: CSR values:
[35722.929743] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[35722.929748] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X40489204
[35722.929752] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X8000ff40
[35722.929757] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[35722.929761] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[35722.929765] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[35722.929770] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[35722.929774] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[35722.929778] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403cd
[35722.929783] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000144
[35722.929788] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[35722.929792] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X80000000
[35722.929797] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X803a0000
[35722.929801] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[35722.929806] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[35722.929810] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[35722.929815] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[35722.929819] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[35722.929823] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000060
[35722.929828] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X882123ee
[35722.929832] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[35722.929836] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[35722.929841] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X3c08019d
[35722.929845] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[35722.929849] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[35722.929851] iwlwifi 0000:03:00.0: FH register values:
[35722.929856] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0cabcb00
[35722.929861] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00cabca0
[35722.929866] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000050
[35722.929870] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[35722.929875] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[35722.929880] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[35722.929884] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[35722.929889] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[35722.929894] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[35722.929993] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[35722.929996] iwlwifi 0000:03:00.0: Status: 0x00000000, count: 6
[35722.929998] iwlwifi 0000:03:00.0: Loaded firmware version: 23.214.9.0
[35722.930001] iwlwifi 0000:03:00.0: 0x00002B03 | ADVANCED_SYSASSERT          
[35722.930004] iwlwifi 0000:03:00.0: 0x002002B0 | uPc
[35722.930006] iwlwifi 0000:03:00.0: 0x00000000 | branchlink1
[35722.930008] iwlwifi 0000:03:00.0: 0x00000BA4 | branchlink2
[35722.930010] iwlwifi 0000:03:00.0: 0x000166A4 | interruptlink1
[35722.930013] iwlwifi 0000:03:00.0: 0x00B55AF8 | interruptlink2
[35722.930015] iwlwifi 0000:03:00.0: 0x00000000 | data1
[35722.930017] iwlwifi 0000:03:00.0: 0xDEADBEEF | data2
[35722.930019] iwlwifi 0000:03:00.0: 0xDEADBEEF | data3
[35722.930021] iwlwifi 0000:03:00.0: 0xE1C16A22 | beacon time
[35722.930023] iwlwifi 0000:03:00.0: 0x9BC6D5D2 | tsf low
[35722.930026] iwlwifi 0000:03:00.0: 0x00000029 | tsf hi
[35722.930028] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[35722.930030] iwlwifi 0000:03:00.0: 0x5C8DF509 | time gp2
[35722.930031] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[35722.930034] iwlwifi 0000:03:00.0: 0x000417D6 | uCode version
[35722.930036] iwlwifi 0000:03:00.0: 0x00000144 | hw version
[35722.930037] iwlwifi 0000:03:00.0: 0x40489204 | board version
[35722.930040] iwlwifi 0000:03:00.0: 0x09B6006F | hcmd
[35722.930042] iwlwifi 0000:03:00.0: 0x000220C0 | isr0
[35722.930044] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[35722.930046] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[35722.930048] iwlwifi 0000:03:00.0: 0x0041C0C0 | isr3
[35722.930051] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[35722.930052] iwlwifi 0000:03:00.0: 0x01000112 | isr_pref
[35722.930054] iwlwifi 0000:03:00.0: 0x00000000 | wait_event
[35722.930056] iwlwifi 0000:03:00.0: 0x00000040 | l2p_control
[35722.930058] iwlwifi 0000:03:00.0: 0x00010000 | l2p_duration
[35722.930060] iwlwifi 0000:03:00.0: 0x0000003F | l2p_mhvalid
[35722.930062] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[35722.930064] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[35722.930066] iwlwifi 0000:03:00.0: 0x18051651 | timestamp
[35722.930069] iwlwifi 0000:03:00.0: 0x00005060 | flow_handler
[35722.982876] iwlwifi 0000:03:00.0: HCMD_ACTIVE already clear for command SCAN_OFFLOAD_CONFIG_CMD
[35722.982909] iwlwifi 0000:03:00.0: FW error in SYNC CMD SCAN_OFFLOAD_CONFIG_CMD
[35722.982968]  [<ffffffffa0347337>] iwl_pcie_send_hcmd_sync+0x4e7/0x500 [iwlwifi]
[35722.982983]  [<ffffffffa0348782>] iwl_trans_pcie_send_hcmd+0x22/0x60 [iwlwifi]
[35722.982992]  [<ffffffffa05324a5>] iwl_mvm_send_cmd+0x45/0xc0 [iwlmvm]
[35722.983001]  [<ffffffffa0539ec7>] iwl_mvm_config_sched_scan+0x1b7/0x3a0 [iwlmvm]
[35722.983015]  [<ffffffffa052bb35>] iwl_mvm_mac_sched_scan_start+0xd5/0x120 [iwlmvm]
[35722.983132]  [<ffffffff8167d079>] netlink_rcv_skb+0xa9/0xd0
[35722.983138]  [<ffffffff8167c5d8>] netlink_unicast+0x128/0x1d0
[35722.983140]  [<ffffffff8167cd14>] netlink_sendmsg+0x364/0x440
[35722.983982] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[35722.984297] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[35730.923628] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[35730.923633] iwlwifi 0000:03:00.0: CSR values:
[35730.923636] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[35730.923641] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X40489204
[35730.923645] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X8000ff40
[35730.923650] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[35730.923654] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[35730.923658] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[35730.923663] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[35730.923667] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[35730.923671] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403cd
[35730.923676] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000144
[35730.923680] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[35730.923685] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X80000000
[35730.923689] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X803a0000
[35730.923694] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[35730.923698] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[35730.923702] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[35730.923707] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[35730.923711] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[35730.923716] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000060
[35730.923720] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X882123ee
[35730.923724] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[35730.923728] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[35730.923733] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X3c08019d
[35730.923737] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[35730.923741] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[35730.923743] iwlwifi 0000:03:00.0: FH register values:
[35730.923748] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0cabcb00
[35730.923753] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00cabca0
[35730.923758] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000020
[35730.923763] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[35730.923768] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[35730.923772] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[35730.923777] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[35730.923782] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[35730.923787] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[35730.923884] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[35730.923887] iwlwifi 0000:03:00.0: Status: 0x00000000, count: 6
[35730.923889] iwlwifi 0000:03:00.0: Loaded firmware version: 23.214.9.0
[35730.923891] iwlwifi 0000:03:00.0: 0x00002B03 | ADVANCED_SYSASSERT          
[35730.923893] iwlwifi 0000:03:00.0: 0x002002F0 | uPc
[35730.923895] iwlwifi 0000:03:00.0: 0x00000000 | branchlink1
[35730.923897] iwlwifi 0000:03:00.0: 0x00000BA4 | branchlink2
[35730.923899] iwlwifi 0000:03:00.0: 0x000166A4 | interruptlink1
[35730.923900] iwlwifi 0000:03:00.0: 0x00B55AF8 | interruptlink2
[35730.923902] iwlwifi 0000:03:00.0: 0x00000000 | data1
[35730.923904] iwlwifi 0000:03:00.0: 0xDEADBEEF | data2
[35730.923906] iwlwifi 0000:03:00.0: 0xDEADBEEF | data3
[35730.923908] iwlwifi 0000:03:00.0: 0x00000000 | beacon time
[35730.923911] iwlwifi 0000:03:00.0: 0x00791CD6 | tsf low
[35730.923913] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[35730.923915] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[35730.923917] iwlwifi 0000:03:00.0: 0x00791CD6 | time gp2
[35730.923920] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[35730.923922] iwlwifi 0000:03:00.0: 0x000417D6 | uCode version
[35730.923924] iwlwifi 0000:03:00.0: 0x00000144 | hw version
[35730.923926] iwlwifi 0000:03:00.0: 0x40489204 | board version
[35730.923928] iwlwifi 0000:03:00.0: 0x0921006F | hcmd
[35730.923930] iwlwifi 0000:03:00.0: 0x00022080 | isr0
[35730.923932] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[35730.923935] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[35730.923937] iwlwifi 0000:03:00.0: 0x0041FCC0 | isr3
[35730.923939] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[35730.923940] iwlwifi 0000:03:00.0: 0x01000112 | isr_pref
[35730.923942] iwlwifi 0000:03:00.0: 0x00000000 | wait_event
[35730.923945] iwlwifi 0000:03:00.0: 0x00000811 | l2p_control
[35730.923947] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[35730.923949] iwlwifi 0000:03:00.0: 0x00000003 | l2p_mhvalid
[35730.923951] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[35730.923953] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[35730.923955] iwlwifi 0000:03:00.0: 0x18051651 | timestamp
[35730.923957] iwlwifi 0000:03:00.0: 0x00002030 | flow_handler
[35730.924220] iwlwifi 0000:03:00.0: FW error in SYNC CMD SCAN_OFFLOAD_CONFIG_CMD
[35730.924275]  [<ffffffffa0347337>] iwl_pcie_send_hcmd_sync+0x4e7/0x500 [iwlwifi]
[35730.924286]  [<ffffffffa0348782>] iwl_trans_pcie_send_hcmd+0x22/0x60 [iwlwifi]
[35730.924293]  [<ffffffffa05324a5>] iwl_mvm_send_cmd+0x45/0xc0 [iwlmvm]
[35730.924301]  [<ffffffffa0539ec7>] iwl_mvm_config_sched_scan+0x1b7/0x3a0 [iwlmvm]
[35730.924306]  [<ffffffffa052bb35>] iwl_mvm_mac_sched_scan_start+0xd5/0x120 [iwlmvm]
[35730.924389]  [<ffffffff8167d079>] netlink_rcv_skb+0xa9/0xd0
[35730.924394]  [<ffffffff8167c5d8>] netlink_unicast+0x128/0x1d0
[35730.924396]  [<ffffffff8167cd14>] netlink_sendmsg+0x364/0x440
[35730.924772] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[35730.925035] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[35731.736060] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[35731.736379] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[35731.747315] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[35834.339529] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[35834.339532] iwlwifi 0000:03:00.0: CSR values:
[35834.339534] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[35834.339538] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X40489204
[35834.339542] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X8000ff40
[35834.339545] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[35834.339549] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[35834.339552] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[35834.339556] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[35834.339559] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[35834.339562] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403cd
[35834.339569] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000144
[35834.339586] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[35834.339589] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X80000000
[35834.339593] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X803a0000
[35834.339596] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[35834.339600] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[35834.339604] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[35834.339607] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[35834.339611] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[35834.339615] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000060
[35834.339618] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X882123ee
[35834.339622] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[35834.339637] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[35834.339641] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X3c08019d
[35834.339644] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[35834.339648] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[35834.339649] iwlwifi 0000:03:00.0: FH register values:
[35834.339653] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0cabcb00
[35834.339657] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00cabca0
[35834.339661] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000050
[35834.339664] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[35834.339668] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[35834.339672] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[35834.339676] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[35834.339680] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[35834.339683] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[35834.339780] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[35834.339781] iwlwifi 0000:03:00.0: Status: 0x00000000, count: 6
[35834.339782] iwlwifi 0000:03:00.0: Loaded firmware version: 23.214.9.0
[35834.339784] iwlwifi 0000:03:00.0: 0x00002B03 | ADVANCED_SYSASSERT          
[35834.339785] iwlwifi 0000:03:00.0: 0x002002F0 | uPc
[35834.339786] iwlwifi 0000:03:00.0: 0x00000000 | branchlink1
[35834.339788] iwlwifi 0000:03:00.0: 0x00000BA4 | branchlink2
[35834.339789] iwlwifi 0000:03:00.0: 0x000166A4 | interruptlink1
[35834.339790] iwlwifi 0000:03:00.0: 0x00B55AF8 | interruptlink2
[35834.339791] iwlwifi 0000:03:00.0: 0x00000000 | data1
[35834.339792] iwlwifi 0000:03:00.0: 0xDEADBEEF | data2
[35834.339793] iwlwifi 0000:03:00.0: 0xDEADBEEF | data3
[35834.339794] iwlwifi 0000:03:00.0: 0x00000000 | beacon time
[35834.339796] iwlwifi 0000:03:00.0: 0x061E5DC1 | tsf low
[35834.339797] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[35834.339798] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[35834.339799] iwlwifi 0000:03:00.0: 0x061E5DC2 | time gp2
[35834.339800] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[35834.339801] iwlwifi 0000:03:00.0: 0x000417D6 | uCode version
[35834.339802] iwlwifi 0000:03:00.0: 0x00000144 | hw version
[35834.339803] iwlwifi 0000:03:00.0: 0x40489204 | board version
[35834.339804] iwlwifi 0000:03:00.0: 0x092B006F | hcmd
[35834.339805] iwlwifi 0000:03:00.0: 0x00022080 | isr0
[35834.339807] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[35834.339808] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[35834.339809] iwlwifi 0000:03:00.0: 0x0041FCC0 | isr3
[35834.339810] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[35834.339811] iwlwifi 0000:03:00.0: 0x01000112 | isr_pref
[35834.339812] iwlwifi 0000:03:00.0: 0x00000000 | wait_event
[35834.339813] iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
[35834.339814] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[35834.339815] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[35834.339816] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[35834.339818] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[35834.339819] iwlwifi 0000:03:00.0: 0x18051651 | timestamp
[35834.339820] iwlwifi 0000:03:00.0: 0x00005060 | flow_handler
[35834.339848] iwlwifi 0000:03:00.0: FW error in SYNC CMD SCAN_OFFLOAD_CONFIG_CMD
[35834.339886]  [<ffffffffa0347337>] iwl_pcie_send_hcmd_sync+0x4e7/0x500 [iwlwifi]
[35834.339900]  [<ffffffffa0348782>] iwl_trans_pcie_send_hcmd+0x22/0x60 [iwlwifi]
[35834.339908]  [<ffffffffa05324a5>] iwl_mvm_send_cmd+0x45/0xc0 [iwlmvm]
[35834.339915]  [<ffffffffa0539ec7>] iwl_mvm_config_sched_scan+0x1b7/0x3a0 [iwlmvm]
[35834.339919]  [<ffffffffa052bb35>] iwl_mvm_mac_sched_scan_start+0xd5/0x120 [iwlmvm]
[35834.340005]  [<ffffffff8167d079>] netlink_rcv_skb+0xa9/0xd0
[35834.340008]  [<ffffffff8167c5d8>] netlink_unicast+0x128/0x1d0
[35834.340010]  [<ffffffff8167cd14>] netlink_sendmsg+0x364/0x440
[35834.341460] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[35834.341712] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[35834.375351] wlan0: authenticate with <MAC C-01 belkin.986>
[35834.376207] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[35834.377896] wlan0: authenticated
[35834.379497] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[35834.459447] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=5)
[35834.464856] wlan0: associated
[35834.464910] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


    ======== Done ========
```

---

### Post by Hadaka on 2014-09-07
Hi, looking at some of your wireless output it looks like
[http://ubuntuforums.org/showthread.php?t=2242147&page=2](http://ubuntuforums.org/showthread.php?t=2242147&page=2)
would help you out. If you are not an experienced user, I would
strongly suggest requesting chili555's  help with this, please
post back if you require help,
thanks

---

### Post by rafael10 on 2014-09-07
ill need help

---

### Post by praseodym on 2014-09-07
Deactivate the N-mode of the driver and the queue:

```
echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by rafael10 on 2014-09-07
ok i did all those commands

---

### Post by chili555 on 2014-09-07
Although modinfo calls for the -8 firmware, the system is loading -9. Then an serious sounding error triggers:> [35834.339780] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[35834.339781] iwlwifi 0000:03:00.0: Status: 0x00000000, count: 6
[35834.339782] iwlwifi 0000:03:00.0: Loaded firmware version: 23.214.9.0
[35834.339784] iwlwifi 0000:03:00.0: 0x00002B03 | ADVANCED_SYSASSERT          
[35834.339785] iwlwifi 0000:03:00.0: 0x002002F0 | uPc
[35834.339786] iwlwifi 0000:03:00.0: 0x00000000 | branchlink1
<sip> Do you also have -8 on your system?```
ls /lib/firmware | grep 7260
```On my system, I have:```
$ ls /lib/firmware | grep 7260
iwlwifi-7260-7.ucode
iwlwifi-7260-8.ucode
iwlwifi-7260-9.ucode
```In other words, I have -7, -8 and -9. If you have the same, please back up your -9:```
sudo mv /lib/firmware/iwlwifi-7260-9.ucode  /lib/firmware/iwlwifi-7260-9.bak
```Reboot and check the log for errors again:```
dmesg | grep iwl
```

---

### Post by rafael10 on 2014-09-07
i got one error ```
loggikwolf@Alpha:~$ dmesg | grep iwl[    9.020567] iwlwifi 0000:03:00.0: irq 64 for MSI/MSI-X
[    9.157389] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[    9.157394] iwlwifi 0000:03:00.0: Falling back to user helper
[    9.591480] iwlwifi 0000:03:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    9.746364] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    9.746411] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    9.746630] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   10.117301] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   18.497395] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   18.497748] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
```

---

### Post by chili555 on 2014-09-07
> **rafael10 said:**
> i got one error Yes, but it loaded the -8 firmware and you did not see the dozens of lines of error messages related to iwlwifi and its firmware. > loaded firmware version 22.24.[COLOR="#FF0000"]8[/COLOR].0 op_mode iwlmvm

Did you connect? Solved? More problems??

---

### Post by rafael10 on 2014-09-07
it seem alright, ill give it a day or two and ill respond if it worked or if it didnt thanks

---

### Post by chili555 on 2014-09-07
Very well. We will appreciate your response in case other 7260 users are having the same difficulty.

---

### Post by Hadaka on 2014-09-07
Hi, hopefully that fixed it ! 
*If your modem is N speed able and configured correctly
and if your problem is fixed, you may want to re-activate the
N function as you currently have it disabled per post #4
to enable,,
```
sudo sed -i '/options iwlwifi 11n_disable=1 wd_disable=1/ d' /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
and if all is well please mark solved
-> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

*Edit: Correction has been made.
thank you Dr. Chili555

---

### Post by chili555 on 2014-09-07
> echo "options iwlwifi 11n_disable=0 wd_disable=0" | sudo tee /etc/modprobe.d/iwlwifi.confThat will wipe out all the preceding text:> # /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod)
&& /sbin/modprobe -r mac80211This you do not want to do! I suggest that you edit the file instead to remove the offending lines. My esteemed colleague Hadaka will show you.

---

### Post by rafael10 on 2014-09-09
i still have the problem, my connection is still really lagy on linux

---

### Post by chili555 on 2014-09-10
> **rafael10 said:**
> i still have the problem, my connection is still really lagy on linuxLet's double-check your conf file:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Amend the file so it reads:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=2
```Proofread carefully, save and close the text editor. Reboot and let us hear your report.

---

### Post by rafael10 on 2014-09-11
i got an error when i did that command ```
loggikwolf@Alpha:~$ gksudo gedit /etc/modprobe.d/iwlwifi.conf

** (gksudo:22752): CRITICAL **: fcntl error


** (gksudo:22752): WARNING **: Lock taken by pid: -1. Exiting.
loggikwolf@Alpha:~$
```

---

### Post by varunendra on 2014-09-11
Just filling in while others are away..

For now, please just show us the contents of your /etc/modprobe.d/iwlwifi.conf file -
```
cat /etc/modprobe.d/iwlwifi.conf
```
..so we can see where we are standing and what is needed to do what has been suggested already.

---

### Post by rafael10 on 2014-09-11
```
loggikwolf@Alpha:~$ cat /etc/modprobe.d/iwlwifi.confoptions iwlwifi 11n_disable=1 wd_disable=1
```

---

### Post by chili555 on 2014-09-11
It seems to have lost quite a bit of text! Please try:```
sudo -i
gedit /etc/modprobe.d/iwlwifi.conf
```Make the file read like this:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8
```Proofread carefully, save and close gedit. Reboot and tell us if there is any improbement.

---

### Post by rafael10 on 2014-09-14
it didnt help it seems the same

---

### Post by varunendra on 2014-09-14
It is always a good idea to show us how the settings/files currently look like so we can be sure there are no unwanted settings or errors.

You could also just run the [wireless_script]("http://ubuntuforums.org/showpost.php?p=13024222") everytime > load its contents to pastebin and post its link here so we can see all the related settings at once.

---

### Post by rafael10 on 2014-09-14
```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Alpha 3.15.0-031500rc3-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7868 MB
Uptime : 09:09:25 up 11:14,  3 users,  load average: 1.92, 2.46, 2.31




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
	Kernel driver in use: iwlwifi




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 010: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 013: ID 8087:07dc Intel Corp. 
Bus 001 Device 012: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abgn  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC C-01 belkin.986>   
          Bit Rate=121.5 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:35   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      yes           no
2: phy0: Wireless LAN             no            no
3: hci0: Bluetooth                yes           no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwlmvm                216368  0 
mac80211              663788  1 iwlmvm
asus_nb_wmi            16990  0 
asus_wmi               24697  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
iwlwifi               181776  1 iwlmvm
cfg80211              509833  3 iwlwifi,mac80211,iwlmvm
wmi                    19379  1 asus_wmi
video                  19932  2 i915,asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=1
iwlwifi      (11): 11n_disable=8 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=====================o=============o=========o====  =========o=========o===========o==============o===  ========
 Interface & ID      | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
=====================o=============o=========o====  =========o=========o===========o==============o===  ========
 wlan0  [belkin.986] | 802.11 WiFi | iwlwifi | connected   | yes     | 121 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>


    2WIRE951:        Infra, <MAC C-03 2WIRE951>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    2WIRE000:        Infra, <MAC C-NA 2WIRE000 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    MyCharterWiFi3f-5G: Infra, <MAC C-NA MyCharterWiFi3f-5G 1>, Freq 5765 MHz, Rate 54 Mb/s, Strength 17 WPA2
    *belkin.986:     Infra, <MAC C-01 belkin.986>, Freq 2427 MHz, Rate 54 Mb/s, Strength 69 WPA2
    MyCharterWiFi3f-2G: Infra, <MAC C-02 MyCharterWiFi3f-2G>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    MyCharterWiFi71-2G: Infra, <MAC C-NA MyCharterWiFi71-2G 1>, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA2


    Address:         192.168.2.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
---------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169   | unavailable | no      |           |              | <MAC eth0>
---------------------+-------------+---------+-------------+---------+-----------+--------------+-----------




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


belkin.986           : ssid=belkin.986 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 192.168.2.1
nameserver 127.0.1.1
search Belkin




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.316/2.264/3.213/0.949 ms


--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 2.250/2.638/3.027/0.391 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.017/0.021/0.025/0.004 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)


          Current Frequency:2.427 GHz (Channel 4)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 belkin.986>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"belkin.986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000091a2d18b8
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 MyCharterWiFi3f-2G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"MyCharterWiFi3f-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001efff19183
                    Extra: Last beacon: 3568ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 2WIRE951>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"2WIRE951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000356eeb63bd
                    Extra: Last beacon: 72ms ago
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




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[iwlmvm]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     7F619E415D8ECAAAD38E153
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/net/mac80211/mac80211.ko
srcversion:     AE7FF15CC48CEBF86450AA1
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[asus_nb_wmi]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
parm:           wapf:WAPF value (uint)


[asus_wmi]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     F1B598E231F902960383641
depends:        sparse-keymap,wmi,video


[iwlwifi]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-8.ucode
firmware:       iwlwifi-3160-8.ucode
firmware:       iwlwifi-7260-8.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     7EEF6B6542F122FA91624B7
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/net/wireless/cfg80211.ko
srcversion:     EE81A925F8AD66571D5F75D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.15.0-031500rc3-generic/kernel/drivers/acpi/video.ko
srcversion:     D25687678246FBE9023F1F2
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modprobe.d]
iwlmvm.conf       : options iwlmvm power_scheme=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=8
iwlwifi.conf~     : options iwlwifi 11n_disable=1 wd_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/power.d/wireless] [executable]
iwconfig wlan0 power off




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.15.0-031500rc3-generic root=UUID=1bac92c1-18ae-4b7a-8223-d2adad876efd ro quiet splash




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.038225] Initializing cgroup subsys net_cls
[    0.904892] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.905298] audit: initializing netlink subsys (disabled)
[    1.066490] wmi: Mapper loaded
[    1.071388] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.137576] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[    7.636443] iwlwifi 0000:03:00.0: irq 64 for MSI/MSI-X
[    7.794865] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[    7.794870] iwlwifi 0000:03:00.0: Falling back to user helper
[    7.973539] iwlwifi 0000:03:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    8.162955] asus_wmi: ASUS WMI generic driver loaded
[    8.165143] asus_wmi: Initialization: 0x1
[    8.165207] asus_wmi: BIOS WMI version: 7.9
[    8.165282] asus_wmi: SFUN value: 0x4a0877
[    8.166312] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input18
[    8.176950] asus_wmi: Backlight controlled by ACPI video driver
[    8.616909] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    8.616955] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    8.617171] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    8.921441] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   15.155893] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.933745] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   17.934084] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   17.944901] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.049474] wlan0: authenticate with <MAC C-01 belkin.986>
[   21.050492] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   21.065353] wlan0: authenticated
[   21.068137] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   21.073900] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[   21.076429] wlan0: associated
[   21.076462] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.877379] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[   30.885090] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   30.885407] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   30.896041] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.657192] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   31.657509] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   31.668105] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.697735] wlan0: authenticate with <MAC C-01 belkin.986>
[   34.698528] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   34.703226] wlan0: authenticated
[   34.704553] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   34.708446] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[   34.718776] wlan0: associated
[   34.718800] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1328.830375] iwlwifi 0000:03:00.0: Drained sta 0, but it is internal?
[ 1331.787874] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1331.788683] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1331.859177] wlan0: send auth to <MAC C-01 belkin.986> (try 2/3)
[ 1331.931185] wlan0: send auth to <MAC C-01 belkin.986> (try 3/3)
[ 1331.974699] wlan0: authentication with <MAC C-01 belkin.986> timed out
[ 1335.338597] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 1335.338602] iwlwifi 0000:03:00.0: CSR values:
[ 1335.338605] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 1335.338609] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X40489204
[ 1335.338614] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X8000ff40
[ 1335.338618] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[ 1335.338623] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 1335.338627] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[ 1335.338631] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[ 1335.338635] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 1335.338640] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403cd
[ 1335.338644] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000144
[ 1335.338648] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[ 1335.338652] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X80000000
[ 1335.338657] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X803a0000
[ 1335.338661] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[ 1335.338665] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 1335.338669] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 1335.338673] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 1335.338678] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 1335.338682] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000060
[ 1335.338686] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X88211e88
[ 1335.338690] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 1335.338695] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[ 1335.338699] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X3c08019d
[ 1335.338703] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 1335.338707] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 1335.338709] iwlwifi 0000:03:00.0: FH register values:
[ 1335.338714] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X21197500
[ 1335.338719] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02119760
[ 1335.338723] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000020
[ 1335.338728] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[ 1335.338733] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 1335.338737] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 1335.338742] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 1335.338747] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 1335.338751] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 1335.338858] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[ 1335.338860] iwlwifi 0000:03:00.0: Status: 0x00000000, count: 6
[ 1335.338862] iwlwifi 0000:03:00.0: Loaded firmware version: 22.24.8.0
[ 1335.338863] iwlwifi 0000:03:00.0: 0x00002B03 | ADVANCED_SYSASSERT          
[ 1335.338865] iwlwifi 0000:03:00.0: 0x002002B0 | uPc
[ 1335.338866] iwlwifi 0000:03:00.0: 0x00000000 | branchlink1
[ 1335.338867] iwlwifi 0000:03:00.0: 0x00000BEA | branchlink2
[ 1335.338869] iwlwifi 0000:03:00.0: 0x00015EB4 | interruptlink1
[ 1335.338870] iwlwifi 0000:03:00.0: 0x00B50008 | interruptlink2
[ 1335.338871] iwlwifi 0000:03:00.0: 0x00000000 | data1
[ 1335.338872] iwlwifi 0000:03:00.0: 0xDEADBEEF | data2
[ 1335.338874] iwlwifi 0000:03:00.0: 0xDEADBEEF | data3
[ 1335.338875] iwlwifi 0000:03:00.0: 0x690058FA | beacon time
[ 1335.338876] iwlwifi 0000:03:00.0: 0xE6F54942 | tsf low
[ 1335.338877] iwlwifi 0000:03:00.0: 0x00000029 | tsf hi
[ 1335.338879] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[ 1335.338880] iwlwifi 0000:03:00.0: 0x4DBF782D | time gp2
[ 1335.338881] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[ 1335.338883] iwlwifi 0000:03:00.0: 0x00041618 | uCode version
[ 1335.338884] iwlwifi 0000:03:00.0: 0x00000144 | hw version
[ 1335.338885] iwlwifi 0000:03:00.0: 0x40489204 | board version
[ 1335.338886] iwlwifi 0000:03:00.0: 0x0958006F | hcmd
[ 1335.338888] iwlwifi 0000:03:00.0: 0x00022080 | isr0
[ 1335.338889] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[ 1335.338890] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[ 1335.338891] iwlwifi 0000:03:00.0: 0x0041C0C0 | isr3
[ 1335.338893] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[ 1335.338894] iwlwifi 0000:03:00.0: 0x01000112 | isr_pref
[ 1335.338895] iwlwifi 0000:03:00.0: 0x00000000 | wait_event
[ 1335.338896] iwlwifi 0000:03:00.0: 0x00004208 | l2p_control
[ 1335.338898] iwlwifi 0000:03:00.0: 0x00010000 | l2p_duration
[ 1335.338899] iwlwifi 0000:03:00.0: 0x0000033F | l2p_mhvalid
[ 1335.338900] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[ 1335.338901] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[ 1335.338903] iwlwifi 0000:03:00.0: 0x23021719 | timestamp
[ 1335.338904] iwlwifi 0000:03:00.0: 0x00002030 | flow_handler
[ 1335.391137] iwlwifi 0000:03:00.0: HCMD_ACTIVE already clear for command SCAN_OFFLOAD_CONFIG_CMD
[ 1335.391157] iwlwifi 0000:03:00.0: FW error in SYNC CMD SCAN_OFFLOAD_CONFIG_CMD
[ 1335.391203]  [<ffffffffa0348337>] iwl_pcie_send_hcmd_sync+0x4e7/0x500 [iwlwifi]
[ 1335.391217]  [<ffffffffa0349782>] iwl_trans_pcie_send_hcmd+0x22/0x60 [iwlwifi]
[ 1335.391225]  [<ffffffffa04924a5>] iwl_mvm_send_cmd+0x45/0xc0 [iwlmvm]
[ 1335.391240]  [<ffffffffa0499ec7>] iwl_mvm_config_sched_scan+0x1b7/0x3a0 [iwlmvm]
[ 1335.391251]  [<ffffffffa048bb35>] iwl_mvm_mac_sched_scan_start+0xd5/0x120 [iwlmvm]
[ 1335.391344]  [<ffffffff8167d079>] netlink_rcv_skb+0xa9/0xd0
[ 1335.391350]  [<ffffffff8167c5d8>] netlink_unicast+0x128/0x1d0
[ 1335.391353]  [<ffffffff8167cd14>] netlink_sendmsg+0x364/0x440
[ 1335.394794] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1335.395110] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1342.503421] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1342.503750] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1342.514596] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1369.056167] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 1369.056175] iwlwifi 0000:03:00.0: CSR values:
[ 1369.056178] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 1369.056185] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X40489204
[ 1369.056191] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X8000ff40
[ 1369.056197] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[ 1369.056202] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 1369.056208] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[ 1369.056213] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[ 1369.056218] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 1369.056224] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403cd
[ 1369.056229] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000144
[ 1369.056235] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[ 1369.056240] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X80000000
[ 1369.056256] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X803a0000
[ 1369.056262] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[ 1369.056267] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 1369.056273] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 1369.056278] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 1369.056283] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 1369.056289] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000060
[ 1369.056294] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X88211e88
[ 1369.056299] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 1369.056304] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[ 1369.056310] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X3c08019d
[ 1369.056315] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 1369.056321] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 1369.056324] iwlwifi 0000:03:00.0: FH register values:
[ 1369.056330] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X21197500
[ 1369.056336] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02119760
[ 1369.056342] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000078
[ 1369.056346] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[ 1369.056351] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 1369.056355] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 1369.056360] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 1369.056364] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 1369.056369] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 1369.056467] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[ 1369.056469] iwlwifi 0000:03:00.0: Status: 0x00000000, count: 6
[ 1369.056471] iwlwifi 0000:03:00.0: Loaded firmware version: 22.24.8.0
[ 1369.056473] iwlwifi 0000:03:00.0: 0x00002B03 | ADVANCED_SYSASSERT          
[ 1369.056475] iwlwifi 0000:03:00.0: 0x002002B0 | uPc
[ 1369.056477] iwlwifi 0000:03:00.0: 0x00000000 | branchlink1
[ 1369.056479] iwlwifi 0000:03:00.0: 0x00000BEA | branchlink2
[ 1369.056480] iwlwifi 0000:03:00.0: 0x00015EB4 | interruptlink1
[ 1369.056482] iwlwifi 0000:03:00.0: 0x00B50008 | interruptlink2
[ 1369.056484] iwlwifi 0000:03:00.0: 0x00000000 | data1
[ 1369.056486] iwlwifi 0000:03:00.0: 0xDEADBEEF | data2
[ 1369.056487] iwlwifi 0000:03:00.0: 0xDEADBEEF | data3
[ 1369.056489] iwlwifi 0000:03:00.0: 0x00000000 | beacon time
[ 1369.056491] iwlwifi 0000:03:00.0: 0x01954888 | tsf low
[ 1369.056492] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[ 1369.056494] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[ 1369.056496] iwlwifi 0000:03:00.0: 0x01954888 | time gp2
[ 1369.056497] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[ 1369.056499] iwlwifi 0000:03:00.0: 0x00041618 | uCode version
[ 1369.056501] iwlwifi 0000:03:00.0: 0x00000144 | hw version
[ 1369.056503] iwlwifi 0000:03:00.0: 0x40489204 | board version
[ 1369.056504] iwlwifi 0000:03:00.0: 0x092B006F | hcmd
[ 1369.056506] iwlwifi 0000:03:00.0: 0x00022080 | isr0
[ 1369.056508] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[ 1369.056509] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[ 1369.056511] iwlwifi 0000:03:00.0: 0x0041FCC0 | isr3
[ 1369.056512] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[ 1369.056514] iwlwifi 0000:03:00.0: 0x01000112 | isr_pref
[ 1369.056516] iwlwifi 0000:03:00.0: 0x00000000 | wait_event
[ 1369.056518] iwlwifi 0000:03:00.0: 0x00000040 | l2p_control
[ 1369.056519] iwlwifi 0000:03:00.0: 0x00010000 | l2p_duration
[ 1369.056521] iwlwifi 0000:03:00.0: 0x0000003F | l2p_mhvalid
[ 1369.056523] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[ 1369.056524] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[ 1369.056526] iwlwifi 0000:03:00.0: 0x23021719 | timestamp
[ 1369.056528] iwlwifi 0000:03:00.0: 0x00007880 | flow_handler
[ 1369.056547] iwlwifi 0000:03:00.0: FW error in SYNC CMD SCAN_OFFLOAD_CONFIG_CMD
[ 1369.056600]  [<ffffffffa0348337>] iwl_pcie_send_hcmd_sync+0x4e7/0x500 [iwlwifi]
[ 1369.056617]  [<ffffffffa0349782>] iwl_trans_pcie_send_hcmd+0x22/0x60 [iwlwifi]
[ 1369.056627]  [<ffffffffa04924a5>] iwl_mvm_send_cmd+0x45/0xc0 [iwlmvm]
[ 1369.056638]  [<ffffffffa0499ec7>] iwl_mvm_config_sched_scan+0x1b7/0x3a0 [iwlmvm]
[ 1369.056645]  [<ffffffffa048bb35>] iwl_mvm_mac_sched_scan_start+0xd5/0x120 [iwlmvm]
[ 1369.056770]  [<ffffffff8167d079>] netlink_rcv_skb+0xa9/0xd0
[ 1369.056777]  [<ffffffff8167c5d8>] netlink_unicast+0x128/0x1d0
[ 1369.056781]  [<ffffffff8167cd14>] netlink_sendmsg+0x364/0x440
[ 1369.057120] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1369.057376] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1402.080604] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 1402.080610] iwlwifi 0000:03:00.0: CSR values:
[ 1402.080612] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 1402.080617] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X40489204
[ 1402.080622] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X8000ff40
[ 1402.080626] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[ 1402.080630] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 1402.080635] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[ 1402.080639] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[ 1402.080643] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 1402.080647] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403cd
[ 1402.080651] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000144
[ 1402.080656] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[ 1402.080660] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X80000000
[ 1402.080664] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X803a0000
[ 1402.080668] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[ 1402.080673] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 1402.080677] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 1402.080681] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 1402.080685] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 1402.080689] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000060
[ 1402.080694] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X88211e88
[ 1402.080698] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 1402.080702] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[ 1402.080707] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0X3c08019d
[ 1402.080712] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 1402.080718] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 1402.080721] iwlwifi 0000:03:00.0: FH register values:
[ 1402.080727] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X21197500
[ 1402.080733] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02119760
[ 1402.080738] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000030
[ 1402.080744] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[ 1402.080749] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 1402.080755] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 1402.080762] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 1402.080768] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 1402.080774] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 1402.080874] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[ 1402.080876] iwlwifi 0000:03:00.0: Status: 0x00000000, count: 6
[ 1402.080878] iwlwifi 0000:03:00.0: Loaded firmware version: 22.24.8.0
[ 1402.080881] iwlwifi 0000:03:00.0: 0x00002B03 | ADVANCED_SYSASSERT          
[ 1402.080883] iwlwifi 0000:03:00.0: 0x002002B0 | uPc
[ 1402.080885] iwlwifi 0000:03:00.0: 0x00000000 | branchlink1
[ 1402.080886] iwlwifi 0000:03:00.0: 0x00000BEA | branchlink2
[ 1402.080888] iwlwifi 0000:03:00.0: 0x00015EB4 | interruptlink1
[ 1402.080890] iwlwifi 0000:03:00.0: 0x00B50008 | interruptlink2
[ 1402.080892] iwlwifi 0000:03:00.0: 0x00000000 | data1
[ 1402.080894] iwlwifi 0000:03:00.0: 0xDEADBEEF | data2
[ 1402.080896] iwlwifi 0000:03:00.0: 0xDEADBEEF | data3
[ 1402.080897] iwlwifi 0000:03:00.0: 0x00000000 | beacon time
[ 1402.080899] iwlwifi 0000:03:00.0: 0x01F81556 | tsf low
[ 1402.080901] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[ 1402.080903] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[ 1402.080905] iwlwifi 0000:03:00.0: 0x01F81556 | time gp2
[ 1402.080906] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[ 1402.080908] iwlwifi 0000:03:00.0: 0x00041618 | uCode version
[ 1402.080910] iwlwifi 0000:03:00.0: 0x00000144 | hw version
[ 1402.080912] iwlwifi 0000:03:00.0: 0x40489204 | board version
[ 1402.080914] iwlwifi 0000:03:00.0: 0x0921006F | hcmd
[ 1402.080915] iwlwifi 0000:03:00.0: 0x00022080 | isr0
[ 1402.080917] iwlwifi 0000:03:00.0: 0x01000000 | isr1
[ 1402.080919] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[ 1402.080921] iwlwifi 0000:03:00.0: 0x0041FCC0 | isr3
[ 1402.080922] iwlwifi 0000:03:00.0: 0x00000000 | isr4
[ 1402.080924] iwlwifi 0000:03:00.0: 0x01000112 | isr_pref
[ 1402.080926] iwlwifi 0000:03:00.0: 0x00000000 | wait_event
[ 1402.080928] iwlwifi 0000:03:00.0: 0x00000080 | l2p_control
[ 1402.080930] iwlwifi 0000:03:00.0: 0x00010000 | l2p_duration
[ 1402.080931] iwlwifi 0000:03:00.0: 0x0000003F | l2p_mhvalid
[ 1402.080933] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[ 1402.080935] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
[ 1402.080937] iwlwifi 0000:03:00.0: 0x23021719 | timestamp
[ 1402.080939] iwlwifi 0000:03:00.0: 0x00003040 | flow_handler
[ 1402.080958] iwlwifi 0000:03:00.0: FW error in SYNC CMD SCAN_OFFLOAD_CONFIG_CMD
[ 1402.081015]  [<ffffffffa0348337>] iwl_pcie_send_hcmd_sync+0x4e7/0x500 [iwlwifi]
[ 1402.081032]  [<ffffffffa0349782>] iwl_trans_pcie_send_hcmd+0x22/0x60 [iwlwifi]
[ 1402.081043]  [<ffffffffa04924a5>] iwl_mvm_send_cmd+0x45/0xc0 [iwlmvm]
[ 1402.081054]  [<ffffffffa0499ec7>] iwl_mvm_config_sched_scan+0x1b7/0x3a0 [iwlmvm]
[ 1402.081062]  [<ffffffffa048bb35>] iwl_mvm_mac_sched_scan_start+0xd5/0x120 [iwlmvm]
[ 1402.081193]  [<ffffffff8167d079>] netlink_rcv_skb+0xa9/0xd0
[ 1402.081201]  [<ffffffff8167c5d8>] netlink_unicast+0x128/0x1d0
[ 1402.081205]  [<ffffffff8167cd14>] netlink_sendmsg+0x364/0x440
[ 1402.082002] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1402.082250] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1402.109211] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1402.110068] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1402.113309] wlan0: authenticated
[ 1402.117262] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1402.210079] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 1402.215896] wlan0: associated
[ 1402.215921] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10029.793416] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[10038.682615] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10038.682928] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10038.693303] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10038.849142] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10038.849799] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10038.860286] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10040.743765] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10040.744105] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10040.759536] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10041.115818] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10041.116184] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10041.129983] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10043.964809] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[10044.479930] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10044.480140] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10047.132360] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[10047.246373] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[10052.067783] wlan0: authenticate with <MAC C-01 belkin.986>
[10052.068610] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10052.070347] wlan0: authenticated
[10052.073245] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10052.077900] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[10052.080475] wlan0: associated
[10052.080555] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10052.860252] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (Reason: 3=DEAUTH_LEAVING)
[10052.866879] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10052.867216] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10052.880336] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10053.572844] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10053.575045] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10053.585929] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10056.790657] wlan0: authenticate with <MAC C-01 belkin.986>
[10056.791465] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10056.793249] wlan0: authenticated
[10056.794540] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10056.800218] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[10056.810337] wlan0: associated
[10056.810359] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


	======== Done ========
```

---

